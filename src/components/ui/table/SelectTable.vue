<script>
import {
  computed,
  reactive,
  provide,
  onMounted,
  watch,
  ref,
  useCssModule,
} from 'vue';

const defaultClassNames = () => ({
  wrap: '',
  head: '',
  body: '',
  caption: '',
  table: '',
  disabled: '',
});

export default {
  props: {
    classNames: {
      Type: Object,
      default() {
        return defaultClassNames();
      },
    },
    once: {
      Type: Boolean,
      default: true,
    },
    label: {
      Type: String,
      default: null,
    },
    captionId: {
      Type: String,
      default: null,
    },
    caption: {
      Type: String,
      default: null,
    },
    disabled: {
      Type: Boolean,
      default: false,
    },
    maxRow: {
      Type: Number,
      default: 5,
    },
    onSelected: {
      Type: Function,
      default() {
        return () => {};
      },
    },
    onUnSelected: {
      Type: Function,
      default() {
        return () => {};
      },
    },
  },
  setup(props, context) {
    let isHeadScroll = false;
    let isBodyScroll = false;

    const state = reactive({
      items: [],
      count: 0,
      once: {
        value: false,
      },
      callback: {},
    });

    const head = ref(null);
    const body = ref(null);

    const customClassNames = computed(() => {
      const { classNames } = props;
      return Object.assign(defaultClassNames(), classNames);
    });

    const isHead = computed(() => {
      return Boolean(context.slots.head);
    });

    const isColgroup = computed(() => {
      return Boolean(context.slots.colgroup);
    });

    const itemsAdd = (obj) => {
      const key = state.count;

      state.items.push(
        Object.assign({}, obj, {
          key,
        })
      );

      state.count++;

      return key;
    };

    const itemsRemove = (key) => {
      const i = state.items.findIndex((item) => item.key === key);

      state.items.splice(i, 1);
    };

    const allSelect = () => {
      if (props.once) {
        if (state.items[0]) {
          state.items[0].select();
        }
      } else {
        state.items.forEach((item) => {
          item.select();
        });
      }
    };

    const allUnSelect = () => {
      state.items.forEach((item) => {
        item.unSelect();
      });
    };

    const headScroll = () => {
      if (isBodyScroll) return;

      isHeadScroll = true;

      body.value.scrollLeft = head.value.scrollLeft;

      isHeadScroll = false;
    };

    const bodyScroll = () => {
      if (isHeadScroll) return;

      isBodyScroll = true;

      head.value.scrollLeft = body.value.scrollLeft;

      isBodyScroll = false;
    };

    onMounted(() => {
      state.once.value = props.once;
      state.callback.onSelected = props.onSelected;
      state.callback.onUnSelected = props.onUnSelected;
    });

    watch(
      () => props.once,
      (cur) => {
        state.once.value = cur;
      }
    );
    watch(
      () => props.onSelected,
      (cur) => {
        state.callback.onSelected = cur;
      }
    );
    watch(
      () => props.onUnSelected,
      (cur) => {
        state.callback.onUnSelected = cur;
      }
    );

    provide('selectTableStyleModule', useCssModule());

    provide('selectTable', {
      items: state.items,
      itemsAdd,
      itemsRemove,
      allSelect,
      allUnSelect,
      once: state.once,
      callback: state.callback,
    });

    return {
      head,
      body,
      customClassNames,
      isHead,
      isColgroup,
      allSelect,
      allUnSelect,
      headScroll,
      bodyScroll,
    };
  },
};
</script>

<template>
  <div
    :class="[
      $style['select-table'],
      {
        [$style['select-table--disabled']]: disabled,
        [customClassNames.disabled]: disabled,
        [$style[`select-table--maxrow-${maxRow}`]]: maxRow,
      },
      customClassNames.wrap,
    ]"
    role="table"
    :aria-label="label"
    :aria-describedby="captionId"
  >
    <div
      :class="[$style['select-table__caption'], customClassNames.caption]"
      :id="captionId"
    >
      {{ caption }}
    </div>
    <div
      v-if="isHead"
      ref="head"
      :class="[$style['select-table__head'], customClassNames.head]"
      @scroll="headScroll"
    >
      <div :class="[$style['basic-table'], customClassNames.table]">
        <table role="rowgroup">
          <colgroup v-if="isColgroup">
            <slot name="colgroup" />
          </colgroup>
          <thead>
            <slot name="head" />
          </thead>
        </table>
      </div>
    </div>
    <div
      ref="body"
      :class="[$style['select-table__body'], customClassNames.body]"
      @scroll="bodyScroll"
    >
      <div :class="[$style['basic-table'], customClassNames.table]">
        <table role="rowgroup">
          <colgroup v-if="isColgroup">
            <slot name="colgroup" />
          </colgroup>
          <tbody>
            <slot />
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<style lang="scss" module>
@import '@/assets/scss/components/ui/table/SelectTable.scss';
</style>
