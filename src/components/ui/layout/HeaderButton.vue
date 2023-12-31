<script>
import { ref, computed, inject } from 'vue';
import { RouterLink, useRouter } from 'vue-router';

import { useUiCommonStore } from '@/stores/ui/common';

import LayerGlobalNav from '@/components/ui/gnb/LayerGlobalNav.vue';
import RoundButton from '@/components/ui/button/RoundButton.vue';

import IconBack from '@/assets/images/common/back-left.svg?component';
import IconPush from '@/assets/images/common/alarm.svg?component';
import IconMenu from '@/assets/images/common/menu.svg?component';
import IconSearch from '@/assets/images/common/search.svg?component';
import IconShare from '@/assets/images/common/share.svg?component';
import IconClose from '@/assets/images/common/close.svg?component';
import IconSetting from '@/assets/images/common/setting.svg?component';
import IconHome from '@/assets/images/common/home.svg?component';
import IconAdd from '@/assets/images/icon/add.svg?component';

export default {
  components: {
    RouterLink,
    LayerGlobalNav,
    RoundButton,
    IconBack,
    IconPush,
    IconMenu,
    IconSearch,
    IconShare,
    IconClose,
    IconSetting,
    IconHome,
    IconAdd,
  },
  props: {
    type: {
      Type: String,
      default: 'menu',
    },
    onClick: {
      Type: Function,
      default() {
        return () => {};
      },
    },
    text: {
      Type: String,
      default: null,
    },
    theme: {
      Type: String,
      default: null,
    },
  },
  setup() {
    const store = {
      ui: {
        common: useUiCommonStore(),
      },
    };

    const styleModule = inject('headerStyleModule');

    const router = useRouter();

    const gnbLayer = ref(null);

    const pushNotice = computed(() => {
      return true;
    });

    const gnbOpen = (e = {}) => {
      gnbLayer.value.layer.open(e.target);
    };

    return {
      store,
      styleModule,
      router,
      pushNotice,
      gnbLayer,
      gnbOpen,
    };
  },
};
</script>

<template>
  <button
    v-if="type === 'back'"
    type="button"
    :class="styleModule['header__button']"
    @click="router.go(-1)"
  >
    <IconBack :class="styleModule['header__button-icon']" />
    <span :class="styleModule['header__button-text']">뒤로가기</span>
  </button>

  <RouterLink
    v-else-if="type === 'push'"
    to=""
    :class="[
      styleModule['header__button'],
      {
        [styleModule['header__button--notice']]: pushNotice,
      },
    ]"
  >
    <IconPush :class="styleModule['header__button-icon']" />
    <span :class="styleModule['header__button-text']">
      알림{{ pushNotice ? ' (신규 알림 있음)' : '' }}
    </span>
  </RouterLink>

  <RouterLink
    v-else-if="type === 'menu' && store.ui.common.isAPP"
    to="/menu"
    :class="styleModule['header__button']"
  >
    <IconMenu :class="styleModule['header__button-icon']" />
    <span :class="styleModule['header__button-text']">메뉴</span>
  </RouterLink>

  <button
    v-else-if="type === 'menu'"
    type="button"
    :class="styleModule['header__button']"
    @click="gnbOpen"
  >
    <IconMenu :class="styleModule['header__button-icon']" />
    <span :class="styleModule['header__button-text']">메뉴</span>
  </button>

  <button
    v-else-if="type === 'menuButton'"
    type="button"
    :class="styleModule['header__button']"
    @click="onClick"
  >
    <IconMenu :class="styleModule['header__button-icon']" />
    <span :class="styleModule['header__button-text']">메뉴</span>
  </button>

  <button
    v-else-if="type === 'search'"
    type="button"
    :class="styleModule['header__button']"
    @click="onClick"
  >
    <IconSearch :class="styleModule['header__button-icon']" />
    <span :class="styleModule['header__button-text']">검색</span>
  </button>

  <button
    v-else-if="type === 'share'"
    type="button"
    :class="styleModule['header__button']"
    @click="onClick"
  >
    <IconShare :class="styleModule['header__button-icon']" />
    <span :class="styleModule['header__button-text']">공유하기</span>
  </button>

  <button
    v-else-if="type === 'close'"
    type="button"
    :class="styleModule['header__button']"
    @click="onClick"
  >
    <IconClose :class="styleModule['header__button-icon']" />
    <span :class="styleModule['header__button-text']">닫기</span>
  </button>

  <RouterLink
    v-else-if="type === 'setting'"
    to="/setting/home"
    :class="styleModule['header__button']"
  >
    <IconSetting :class="styleModule['header__button-icon']" />
    <span :class="styleModule['header__button-text']">설정</span>
  </RouterLink>

  <button
    v-else-if="type === 'homeButton'"
    type="button"
    :class="styleModule['header__button']"
    @click="onClick"
  >
    <IconHome :class="styleModule['header__button-icon']" />
    <span :class="styleModule['header__button-text']">홈</span>
  </button>

  <RoundButton
    v-else-if="type === 'addButton'"
    theme="secondary"
    @click="onClick"
    :classNames="{
      wrap: styleModule['header__round-button'],
    }"
  >
    <template v-slot:leftIcon>
      <IconAdd />
    </template>
    등록
  </RoundButton>

  <RoundButton
    v-else-if="type === 'roundButton'"
    :theme="theme"
    @click="onClick"
    :classNames="{
      wrap: styleModule['header__round-button'],
    }"
  >
    {{ text }}
  </RoundButton>

  <LayerGlobalNav
    ref="gnbLayer"
    v-if="type === 'menu' && !store.ui.common.isAPP"
  />
</template>
