<script>
// Company_M08_p009
import { onMounted, onUnmounted } from 'vue';

import { useUiHeaderStore } from '@/stores/ui/header';

import PageContents from '@/components/ui/layout/PageContents.vue';
import UiTab from '@/components/ui/tab/UiTab.vue';
import UiTabPanel from '@/components/ui/tab/UiTabPanel.vue';
import NavTab from '@/components/ui/tab/NavTab.vue';
import NavTabButton from '@/components/ui/tab/NavTabButton.vue';
import StickyBar from '@/components/ui/common/StickyBar.vue';

export default {
  components: {
    PageContents,
    UiTab,
    UiTabPanel,
    NavTab,
    NavTabButton,
    StickyBar,
  },
  setup() {
    const store = {
      ui: {
        header: useUiHeaderStore(),
      },
    };

    onMounted(() => {
      store.ui.header.setTitle(() => '하나금융그룹');
      store.ui.header.setLeftButtons(() => ['back']);
      store.ui.header.setRightButtons(() => []);
    });

    onUnmounted(() => {
      store.ui.header.setTitle();
      store.ui.header.setLeftButtons();
      store.ui.header.setRightButtons();
    });
  },
};
</script>

<template>
  <UiTab>
    <PageContents>
      <template v-slot:head>
        <StickyBar>
          <NavTab :head="true" :useUiTab="true">
            <NavTabButton link="companyGroupTab001">비전과 미션</NavTabButton>
            <NavTabButton link="companyGroupTab002">핵심가치</NavTabButton>
            <NavTabButton link="companyGroupTab003">관계사</NavTabButton>
          </NavTab>
        </StickyBar>
      </template>

      <UiTabPanel name="companyGroupTab001">
        <div :class="$style['image-view']">
          <img src="@/assets/images/contents/company-1.png" alt="" />
        </div>
      </UiTabPanel>

      <UiTabPanel name="companyGroupTab002">
        <section class="row-margin-contents-group">
          <h3 class="text-title-1 font-weight-medium row-margin-item">
            <span class="color-green">POWER</span> on Integrity
          </h3>
          <p class="text-body-3 font-weight-light color-gray-tertiary">
            하나금융그룹은 하나인만의 생각하는 방식, 창조적이고 강력한
            기업문화를 가지고 있습니다. 하나인들이 공유하고 실천하는 핵심가치는
            기업 활동에 있어서 가치판단과 행동의 기준이 되는 가장 소중한
            무형자산입니다.
          </p>
        </section>
        <div :class="$style['image-view']">
          <img src="@/assets/images/contents/company-2.png" alt="" />
        </div>
      </UiTabPanel>

      <UiTabPanel name="companyGroupTab003">
        <div :class="$style['image-view']">
          <img src="@/assets/images/contents/company-3.png" alt="" />
        </div>
      </UiTabPanel>
    </PageContents>
  </UiTab>
</template>

<style lang="scss" module>
@import '@/assets/scss/views/company/CompanyGroup.scss';
</style>
