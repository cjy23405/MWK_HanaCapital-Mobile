<script>
// EL_M01_l001
import { ref } from 'vue';

import UiLayer from '@/components/ui/layer/UiLayer.vue';
import PopupTitle from '@/components/ui/layer/PopupTitle.vue';
import PopupButton from '@/components/ui/layer/PopupButton.vue';
import FullPopup from '@/components/ui/layer/FullPopup.vue';
import FullPopupHead from '@/components/ui/layer/FullPopupHead.vue';
import BasicButton from '@/components/ui/button/BasicButton.vue';
import ButtonList from '@/components/ui/button/ButtonList.vue';
import ButtonListItem from '@/components/ui/button/ButtonListItem.vue';

export default {
  components: {
    UiLayer,
    PopupTitle,
    PopupButton,
    FullPopup,
    FullPopupHead,
    BasicButton,
    ButtonList,
    ButtonListItem,
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
          <PopupTitle>예상 상환스케쥴</PopupTitle>
          <template v-slot:right>
            <PopupButton @click="layerSlotProps.close()" />
          </template>
        </FullPopupHead>
      </template>

      <ul :class="$style['bill-list']">
        <li v-for="i in 7" :key="i" :class="$style['bill-list__item']">
          <div :class="$style['bill-list__block']">
            <div :class="$style['bill-list__head']">
              <div :class="$style['bill-list__detail']">
                <span :class="$style['bill-list__detail-item']"
                  >{{ i }}회차</span
                >
              </div>
              <div :class="$style['bill-list__amount']">1,232,456,345 원</div>
            </div>
            <div :class="$style['bill-list__contents']">
              <div :class="$style['bill-list__contents-left']">
                <dl :class="$style['bill-list__sub']">
                  <div :class="$style['bill-list__sub-item']">
                    <dt :class="$style['bill-list__sub-key']">원금</dt>
                    <dd :class="$style['bill-list__sub-value']">
                      912,232,321 원
                    </dd>
                  </div>
                  <div :class="$style['bill-list__sub-item']">
                    <dt :class="$style['bill-list__sub-key']">이자</dt>
                    <dd :class="$style['bill-list__sub-value']">
                      902,123,223 원
                    </dd>
                  </div>
                </dl>
              </div>
              <div :class="$style['bill-list__contents-right']">
                <dl :class="$style['bill-list__sub']">
                  <div :class="$style['bill-list__sub-item']">
                    <dt :class="$style['bill-list__sub-key']">잔액</dt>
                    <dd :class="$style['bill-list__sub-value']">
                      982,232,123 원
                    </dd>
                  </div>
                </dl>
              </div>
            </div>
          </div>
        </li>
      </ul>

      <template v-slot:foot>
        <ButtonList
          :classNames="{
            wrap: 'row-margin-none',
          }"
        >
          <ButtonListItem>
            <BasicButton>확인</BasicButton>
          </ButtonListItem>
        </ButtonList>
      </template>
    </FullPopup>
  </UiLayer>
</template>

<style lang="scss" module>
@import '@/assets/scss/views/equipmentLease/LayerEquipmentLeaseEstimateSchedule.scss';
</style>
