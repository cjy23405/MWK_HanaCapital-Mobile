<script>
// My_M03_l288
import { ref } from 'vue';

import UiLayer from '@/components/ui/layer/UiLayer.vue';
import FullPopup from '@/components/ui/layer/FullPopup.vue';
import FullPopupHead from '@/components/ui/layer/FullPopupHead.vue';
import PopupTitle from '@/components/ui/layer/PopupTitle.vue';
import PopupButton from '@/components/ui/layer/PopupButton.vue';
import PageTextGroup from '@/components/ui/text/PageTextGroup.vue';
import PageMainText from '@/components/ui/text/PageMainText.vue';
import IllustObject from '@/components/ui/common/IllustObject.vue';
import ButtonList from '@/components/ui/button/ButtonList.vue';
import ButtonListItem from '@/components/ui/button/ButtonListItem.vue';
import BasicButton from '@/components/ui/button/BasicButton.vue';

export default {
  components: {
    UiLayer,
    FullPopup,
    FullPopupHead,
    PopupTitle,
    PopupButton,
    PageTextGroup,
    PageMainText,
    IllustObject,
    ButtonList,
    ButtonListItem,
    BasicButton,
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
          <PopupTitle>일반리스 중요사항 안내</PopupTitle>
          <template v-slot:right>
            <PopupButton @click="layerSlotProps.close()" />
          </template>
        </FullPopupHead>
      </template>

      <PageTextGroup>
        <PageMainText>
          대출금을 만기 전에 상환하고 싶은데 <br />
          가능한가요?
        </PageMainText>
      </PageTextGroup>

      <IllustObject
        type="repayment"
        :classNames="{ wrap: 'row-margin-none' }"
      />

      <div>
        <div class="text-body-2">
          <span class="font-weight-medium">금융리스</span>의 경우
          <span class="color-red">
            계약이 성립한 날로부터 3년 경과 후에도 중도상환수수료가 부과(물건
            매입 시 규정손해배상금)</span
          >되니 확인해야 해요!
        </div>

        <section class="row-margin-contents">
          <div class="color-gray-secondary text-body-4">규정손해배상금</div>
          <ul :class="[$style['basic-list'], 'row-margin-mini']">
            <li
              :class="[
                $style['basic-list__item'],
                'text-body-4',
                'color-black',
                'font-weight-regular',
              ]"
            >
              <div :class="$style['basic-list__symbol']">-</div>
              <div :class="$style['basic-list__content']">
                미회수원금 x 규정손해배상금률
              </div>
            </li>
          </ul>
        </section>
        <section>
          <div class="color-gray-secondary text-body-4">규정손해배상금률</div>
          <ul :class="[$style['basic-list'], 'row-margin-mini']">
            <li
              :class="[
                $style['basic-list__item'],
                'text-body-4',
                'color-black',
                'font-weight-regular',
              ]"
            >
              <div :class="$style['basic-list__symbol']">-</div>
              <div :class="$style['basic-list__content']">
                미회수원금 x 102%
              </div>
            </li>
          </ul>
        </section>
      </div>

      <template v-slot:foot>
        <ButtonList
          :classNames="{
            wrap: 'row-margin-none',
          }"
        >
          <ButtonListItem>
            <BasicButton :line="true" theme="quaternary">이전</BasicButton>
          </ButtonListItem>
          <ButtonListItem>
            <BasicButton>확인했습니다</BasicButton>
          </ButtonListItem>
        </ButtonList>
      </template>
    </FullPopup>
  </UiLayer>
</template>

<style lang="scss" module>
@import '@/assets/scss/views/myLoan/LayerMyLoanOnlineContractDescription009_003.scss';
</style>
