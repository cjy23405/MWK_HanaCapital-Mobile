<script>
import { computed } from 'vue';
import { RouterLink } from 'vue-router';

import IconCloseSmall from '@/assets/images/icon/close-small.svg?component';

const defaultClassNames = () => ({
  wrap: '',
  text: '',
  icon: '',
});

export default {
  inheritAttrs: false,
  components: {
    IconCloseSmall,
  },
  props: {
    classNames: {
      Type: Object,
      default() {
        return defaultClassNames();
      },
    },
    tagName: {
      Type: String,
      default: 'button',
    },
    type: {
      Type: String,
      default: 'button',
    },
    theme: {
      Type: String,
      default: null,
    },
    text: {
      Type: String,
      default: '삭제',
    },
  },
  setup(props) {
    const customClassNames = computed(() => {
      const { classNames } = props;
      return Object.assign(defaultClassNames(), classNames);
    });

    const setComponent = computed(() => {
      const { tagName } = props;
      return tagName === 'RouterLink' ? RouterLink : tagName;
    });

    const setType = computed(() => {
      const { tagName, type } = props;
      return tagName === 'button' ? type : null;
    });

    return {
      customClassNames,
      setComponent,
      setType,
    };
  },
};
</script>

<template>
  <component
    :is="setComponent"
    v-bind="$attrs"
    :type="setType"
    :class="[
      $style['button'],
      {
        [$style[`button--theme-${theme}`]]: theme,
      },
      customClassNames.wrap,
    ]"
  >
    <span :class="[$style['button__icon'], customClassNames.icon]">
      <IconCloseSmall />
    </span>
    <span :class="[$style['button__text'], customClassNames.text]">
      {{ text }}
    </span>
  </component>
</template>

<style lang="scss" module>
@import '@/assets/scss/components/ui/button/DeleteButton.scss';
</style>
