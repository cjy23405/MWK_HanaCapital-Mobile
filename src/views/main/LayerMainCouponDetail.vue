<script>
// Main_M05_l003
import { ref } from 'vue';

import UiLayer from '@/components/ui/layer/UiLayer.vue';
import PopupButton from '@/components/ui/layer/PopupButton.vue';
import FullPopup from '@/components/ui/layer/FullPopup.vue';
import FullPopupHead from '@/components/ui/layer/FullPopupHead.vue';
import BasicButton from '@/components/ui/button/BasicButton.vue';
import ButtonList from '@/components/ui/button/ButtonList.vue';
import ButtonListItem from '@/components/ui/button/ButtonListItem.vue';
import CouponLogo from '@/components/ui/imageData/CouponLogo.vue';

import IconDownload from '@/assets/images/icon/download.svg?component';

export default {
  components: {
    UiLayer,
    PopupButton,
    FullPopup,
    FullPopupHead,
    BasicButton,
    ButtonList,
    ButtonListItem,
    CouponLogo,
    IconDownload,
  },
  setup() {
    const layer = ref(null);

    return {
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
          쿠폰
          <template v-slot:right>
            <PopupButton @click="layerSlotProps.close()" />
          </template>
        </FullPopupHead>
      </template>

      <div :class="$style['coupon-detail']">
        <div :class="$style['coupon-detail__head']">
          <div :class="$style['coupon-detail__left']">
            <CouponLogo src="/images/_dummy/logo-sample.png" />
          </div>
          <div :class="$style['coupon-detail__right']">
            <p :class="$style['coupon-detail__brand-name']">스타벅스</p>
            <h3 :class="$style['coupon-detail__title']">
              디카페인 콜드브루 라떼 T 쿠폰
            </h3>
          </div>
        </div>

        <section :class="$style['coupon-detail__contents']">
          <div :class="$style['image-view']">
            <img src="@/assets/images/_dummy/image-001.png" alt="샘플 이미지" />
          </div>
        </section>
      </div>

      <template v-slot:foot>
        <ButtonList
          :classNames="{
            wrap: 'row-margin-none',
          }"
        >
          <ButtonListItem>
            <BasicButton tagName="a" href="/foo/bar.png" download>
              <template v-slot:leftIcon>
                <IconDownload />
              </template>
              교환권 저장
            </BasicButton>
          </ButtonListItem>
        </ButtonList>
      </template>
    </FullPopup>
  </UiLayer>
</template>

<style lang="scss" module>
@import '@/assets/scss/views/main/LayerMainCouponDetail.scss';
</style>
