<script>
// IF_M02_l003
import { ref } from 'vue';

import UiLayer from '@/components/ui/layer/UiLayer.vue';
import FullPopup from '@/components/ui/layer/FullPopup.vue';
import FullPopupHead from '@/components/ui/layer/FullPopupHead.vue';
import PopupTitle from '@/components/ui/layer/PopupTitle.vue';
import PopupButton from '@/components/ui/layer/PopupButton.vue';
import ButtonList from '@/components/ui/button/ButtonList.vue';
import ButtonListItem from '@/components/ui/button/ButtonListItem.vue';
import BasicButton from '@/components/ui/button/BasicButton.vue';

import IconImgColor from '@/assets/images/icon/img-color.svg?component';

export default {
  components: {
    UiLayer,
    FullPopup,
    FullPopupHead,
    PopupTitle,
    PopupButton,
    ButtonList,
    ButtonListItem,
    BasicButton,
    IconImgColor,
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
          <PopupTitle>고객서류확인</PopupTitle>
          <template v-slot:right>
            <PopupButton @click="layerSlotProps.close()" />
          </template>
        </FullPopupHead>
      </template>

      <div :class="$style['upload-file']">
        <ul :class="$style['upload-file__list']">
          <li :class="$style['upload-file__item']">
            <div :class="$style['upload-file__icon']">
              <IconImgColor />
            </div>
            <div :class="$style['upload-file__content']">
              <div :class="$style['upload-file__name']">
                자동차등록증(필수).jpg
              </div>
              <div :class="$style['upload-file__date']">
                2023-05-08 18:15:44
              </div>
            </div>
            <div :class="$style['upload-file__button']">
              <BasicButton :line="true" theme="quaternary" size="mini">
                미리보기
              </BasicButton>
            </div>
          </li>
          <li :class="$style['upload-file__item']">
            <div :class="$style['upload-file__icon']">
              <IconImgColor />
            </div>
            <div :class="$style['upload-file__content']">
              <div :class="$style['upload-file__name']">기타서류.png</div>
              <div :class="$style['upload-file__date']">
                2023-05-08 18:15:44
              </div>
            </div>
            <div :class="$style['upload-file__button']">
              <BasicButton :line="true" theme="quaternary" size="mini">
                미리보기
              </BasicButton>
            </div>
          </li>
          <li :class="$style['upload-file__item']">
            <div :class="$style['upload-file__icon']">
              <IconImgColor />
            </div>
            <div :class="$style['upload-file__content']">
              <div :class="$style['upload-file__name']">기타서류.gif</div>
              <div :class="$style['upload-file__date']">
                2023-05-08 18:15:44
              </div>
            </div>
            <div :class="$style['upload-file__button']">
              <BasicButton :line="true" theme="quaternary" size="mini">
                미리보기
              </BasicButton>
            </div>
          </li>
        </ul>
      </div>

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
@import '@/assets/scss/views/inventoryFinance/LayerInventoryFinanceLoanConfirmDocument.scss';
</style>
