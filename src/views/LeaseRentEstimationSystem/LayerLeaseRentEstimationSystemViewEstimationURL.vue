<script>
// LR_M00_l003
import { ref } from 'vue';

import UiLayer from '@/components/ui/layer/UiLayer.vue';
import FullPopup from '@/components/ui/layer/FullPopup.vue';
import FullPopupHead from '@/components/ui/layer/FullPopupHead.vue';
import PopupTitle from '@/components/ui/layer/PopupTitle.vue';
import PopupButton from '@/components/ui/layer/PopupButton.vue';
import CheckBox from '@/components/ui/form/CheckBox.vue';
import CheckBoxObject from '@/components/ui/form/CheckBoxObject.vue';
import CheckBoxLabelText from '@/components/ui/form/CheckBoxLabelText.vue';
import DocumentView from '@/components/ui/viewer/DocumentView.vue';

import DocumentEstimate001Contents from '@/views/document/DocumentEstimate001Contents.vue';
import DocumentEstimate002Contents from '@/views/document/DocumentEstimate002Contents.vue';
import DocumentEstimate003Contents from '@/views/document/DocumentEstimate003Contents.vue';
import DocumentEstimate004Contents from '@/views/document/DocumentEstimate004Contents.vue';

import IconPdfDownload from '@/assets/images/icon/pdf-download.svg?component';
import IconJpgDownload from '@/assets/images/icon/jpg-download.svg?component';
import IconPrint from '@/assets/images/icon/print.svg?component';

import dummyDataEstimate from '@/assets/_dummyData/견적서asis/견적서HTML샘플(렌트_장기렌트).html?raw';

export default {
  components: {
    UiLayer,
    FullPopup,
    FullPopupHead,
    PopupTitle,
    PopupButton,
    CheckBox,
    CheckBoxObject,
    CheckBoxLabelText,
    DocumentView,
    DocumentEstimate001Contents,
    DocumentEstimate002Contents,
    DocumentEstimate003Contents,
    DocumentEstimate004Contents,
    IconPdfDownload,
    IconJpgDownload,
    IconPrint,
  },
  setup() {
    const layer = ref(null);

    return {
      dummyDataEstimate,
      layer,
    };
  },
};
</script>

<template>
  <UiLayer ref="layer" type="full" v-slot="layerSlotProps">
    <FullPopup>
      <template v-slot:head>
        <FullPopupHead>
          <PopupTitle>견적서 보기</PopupTitle>
          <template v-slot:right>
            <PopupButton @click="layerSlotProps.close()" />
          </template>
        </FullPopupHead>
      </template>

      <div :class="[$style['share-list'], $style['share-list--col-3']]">
        <ul :class="$style['share-list__list']">
          <li :class="$style['share-list__item']">
            <a
              href="/foo/bar.pdf"
              download
              :class="$style['share-list__button']"
            >
              <span :class="$style['share-list__icon']">
                <IconPdfDownload />
              </span>
              <span :class="$style['share-list__text']">PDF 다운로드</span>
            </a>
          </li>
          <li :class="$style['share-list__item']">
            <a
              href="/foo/bar.pdf"
              download
              :class="$style['share-list__button']"
            >
              <span :class="$style['share-list__icon']">
                <IconJpgDownload />
              </span>
              <span :class="$style['share-list__text']">JPG 다운로드</span>
            </a>
          </li>
          <li :class="$style['share-list__item']">
            <button type="button" :class="$style['share-list__button']">
              <span :class="$style['share-list__icon']">
                <IconPrint />
              </span>
              <span :class="$style['share-list__text']">인쇄</span>
            </button>
          </li>
        </ul>
      </div>

      <div
        class="row-margin-contents-group"
        v-if="layerSlotProps.display !== 'none'"
      >
        <CheckBox
          id="layerLeaseRentEstimationSystemViewEstimationURLCheck001"
          theme="tertiary"
          :classNames="{ wrap: 'row-margin-item-group' }"
        >
          <CheckBoxObject />
          <CheckBoxLabelText>연락처 표시</CheckBoxLabelText>
        </CheckBox>

        <!-- Case : AS-IS -->
        <DocumentView>
          <article
            :class="$style['document']"
            v-html="dummyDataEstimate"
          ></article>
        </DocumentView>
        <!-- // Case : AS-IS -->

        <!-- Case : TO-BE -->
        <DocumentView>
          <DocumentEstimate001Contents />
          <DocumentEstimate002Contents />
          <DocumentEstimate003Contents />
          <DocumentEstimate004Contents />
        </DocumentView>
        <!-- // Case : TO-BE -->
      </div>
    </FullPopup>
  </UiLayer>
</template>

<style lang="scss" module>
@import '@/assets/scss/views/LeaseRentEstimationSystem/LayerLeaseRentEstimationSystemViewEstimationURL.scss';
</style>
