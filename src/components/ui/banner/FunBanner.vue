<script>
import { computed, reactive, watch } from 'vue';
import { RouterLink } from 'vue-router';

const BASE_URL = import.meta.env.BASE_URL;

const defaultClassNames = () => ({
  wrap: '',
  contents: '',
  thumb: '',
  thumbImg: '',
  button: '',
  buttonText: '',
});

export default {
  inheritAttrs: false,
  props: {
    tagName: {
      Type: String,
      default: 'button',
    },
    type: {
      Type: String,
      default: 'button',
    },
    classNames: {
      Type: Object,
      default() {
        return defaultClassNames();
      },
    },
    buttonText: {
      Type: String,
      default: '상세보기',
    },
    thumb: {
      Type: String,
      default: null,
    },
    action: {
      Type: Boolean,
      default: true,
    },
    disabled: {
      Type: Boolean,
      default: false,
    },
    disabledStyle: {
      Type: Boolean,
      default: false,
    },
  },
  setup(props) {
    const state = reactive({
      isError: false,
    });

    const setComponent = computed(() => {
      const { tagName } = props;
      return tagName === 'RouterLink' ? RouterLink : tagName;
    });

    const setType = computed(() => {
      const { tagName, type } = props;
      return tagName === 'button' ? type : null;
    });

    const customClassNames = computed(() => {
      const { classNames } = props;
      return Object.assign(defaultClassNames(), classNames);
    });

    const imgSrc = computed(() => {
      const { thumb = '' } = props;

      if (thumb.match(/^\//)) {
        return BASE_URL + thumb.replace(/^\//, '');
      } else {
        return thumb;
      }
    });

    const onError = () => {
      state.isError = true;
    };

    watch(
      () => props.thumb,
      () => {
        state.isError = false;
      }
    );

    return {
      state,
      setComponent,
      setType,
      customClassNames,
      imgSrc,
      onError,
    };
  },
};
</script>

<template>
  <div
    :class="[
      $style['banner'],
      {
        [$style['banner--disabled']]: disabled || disabledStyle,
      },
      customClassNames.wrap,
    ]"
  >
    <div :class="[$style['banner__contents'], customClassNames.contents]">
      <slot />
    </div>
    <div
      v-if="thumb"
      :class="[$style['banner__thumb'], customClassNames.thumb]"
    >
      <div
        :class="[
          $style['banner__thumb-img'],
          {
            'is-error': state.isError,
          },
          customClassNames.thumbImg,
        ]"
        :style="{
          backgroundImage: `url('${thumb}')`,
        }"
      >
        <img :src="imgSrc" @error="onError" />
      </div>
    </div>
    <component
      :is="setComponent"
      v-if="!disabled && action"
      v-bind="$attrs"
      :type="setType"
      :class="[$style['banner__button'], customClassNames.button]"
    >
      <span
        :class="[$style['banner__button-text'], customClassNames.buttonText]"
        >{{ buttonText }}</span
      >
    </component>
  </div>
</template>

<style lang="scss" module>
@import '@/assets/scss/components/ui/banner/FunBanner.scss';
</style>
