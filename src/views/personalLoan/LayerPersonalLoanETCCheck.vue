<script>
// PF_M11_l007
import { ref, reactive } from 'vue';

import UiLayer from '@/components/ui/layer/UiLayer.vue';
import PopupButton from '@/components/ui/layer/PopupButton.vue';
import FullPopup from '@/components/ui/layer/FullPopup.vue';
import FullPopupHead from '@/components/ui/layer/FullPopupHead.vue';
import PageTextGroup from '@/components/ui/text/PageTextGroup.vue';
import PageMainText from '@/components/ui/text/PageMainText.vue';
import BasicButton from '@/components/ui/button/BasicButton.vue';
import ButtonList from '@/components/ui/button/ButtonList.vue';
import ButtonListItem from '@/components/ui/button/ButtonListItem.vue';
import BoxCheck from '@/components/ui/form/BoxCheck.vue';
import BoxCheckLabel from '@/components/ui/form/BoxCheckLabel.vue';
import BoxCheckList from '@/components/ui/form/BoxCheckList.vue';
import BoxCheckListItem from '@/components/ui/form/BoxCheckListItem.vue';
import KeyValue from '@/components/ui/text/KeyValue.vue';
import KeyValueItem from '@/components/ui/text/KeyValueItem.vue';
import KeyValueTitle from '@/components/ui/text/KeyValueTitle.vue';
import KeyValueText from '@/components/ui/text/KeyValueText.vue';
import BasicHr from '@/components/ui/common/BasicHr.vue';

import IconCalculate from '@/assets/images/icon/calculate.svg?component';

export default {
  components: {
    UiLayer,
    PopupButton,
    FullPopup,
    FullPopupHead,
    PageTextGroup,
    PageMainText,
    BasicButton,
    ButtonList,
    ButtonListItem,
    BoxCheck,
    BoxCheckLabel,
    BoxCheckList,
    BoxCheckListItem,
    KeyValue,
    KeyValueItem,
    KeyValueTitle,
    KeyValueText,
    BasicHr,

    IconCalculate,
  },
  setup() {
    const state = reactive({
      typeError: false,
      sumError: false,
      termError: false,
      interestRateError: false,
    });

    const layer = ref(null);

    return {
      state,
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
          <template v-slot:right>
            <PopupButton @click="layerSlotProps.close()" />
          </template>
        </FullPopupHead>
      </template>

      <PageTextGroup>
        <PageMainText>
          김하나님을 위한<br />
          <strong>한도와 금리가 확인되었습니다</strong>
        </PageMainText>
      </PageTextGroup>

      <div>
        <BoxCheckList align="full">
          <BoxCheckListItem>
            <BoxCheck
              :contents="true"
              name="layerPersonalLoanETCCheckType"
              id="layerPersonalLoanETCCheckType_001"
              :defaultChecked="true"
            >
              <BoxCheckLabel>e하나신용대출</BoxCheckLabel>
              <KeyValue
                margin="mini"
                :classNames="{
                  wrap: 'row-margin-item',
                }"
              >
                <KeyValueItem
                  :classNames="{
                    item: 'text-body-5',
                  }"
                >
                  <KeyValueTitle>최대 한도</KeyValueTitle>
                  <KeyValueText>7,000만원</KeyValueText>
                </KeyValueItem>

                <KeyValueItem
                  :classNames="{
                    item: 'text-body-5',
                  }"
                >
                  <KeyValueTitle>예상 금리</KeyValueTitle>
                  <KeyValueText>15.1% (00개월 기준)</KeyValueText>
                </KeyValueItem>
              </KeyValue>
            </BoxCheck>
          </BoxCheckListItem>
          <BoxCheckListItem>
            <BoxCheck
              :contents="true"
              name="layerPersonalLoanETCCheckType"
              id="layerPersonalLoanETCCheckType_002"
            >
              <BoxCheckLabel
                :classNames="{
                  label: 'font-weight-medium',
                }"
                >행복아파트론</BoxCheckLabel
              >
              <KeyValue
                margin="mini"
                :classNames="{
                  wrap: 'row-margin-item',
                }"
              >
                <KeyValueItem
                  :classNames="{
                    item: 'text-body-5',
                  }"
                >
                  <KeyValueTitle>최대 한도</KeyValueTitle>
                  <KeyValueText>5,000만원</KeyValueText>
                </KeyValueItem>

                <KeyValueItem
                  :classNames="{
                    item: 'text-body-5',
                  }"
                >
                  <KeyValueTitle>예상 금리</KeyValueTitle>
                  <KeyValueText>17.1% (00개월 기준)</KeyValueText>
                </KeyValueItem>
              </KeyValue>
            </BoxCheck>
          </BoxCheckListItem>
          <BoxCheckListItem>
            <BoxCheck
              :contents="true"
              name="layerPersonalLoanETCCheckType"
              id="layerPersonalLoanETCCheckType_003"
            >
              <BoxCheckLabel
                :classNames="{
                  label: 'font-weight-medium',
                }"
                >원큐자동차담보대출</BoxCheckLabel
              >
              <KeyValue
                margin="mini"
                :classNames="{
                  wrap: 'row-margin-item',
                }"
              >
                <KeyValueItem
                  :classNames="{
                    item: 'text-body-5',
                  }"
                >
                  <KeyValueTitle>최대 한도</KeyValueTitle>
                  <KeyValueText>7,000만원</KeyValueText>
                </KeyValueItem>

                <KeyValueItem
                  :classNames="{
                    item: 'text-body-5',
                  }"
                >
                  <KeyValueTitle>예상 금리</KeyValueTitle>
                  <KeyValueText>17.1% (00개월 기준)</KeyValueText>
                </KeyValueItem>
              </KeyValue>
            </BoxCheck>
          </BoxCheckListItem>
        </BoxCheckList>

        <ul :class="[$style['basic-list'], 'row-margin-contents']">
          <li :class="[$style['basic-list__item']]">
            <div :class="$style['basic-list__symbol']"></div>
            <div :class="$style['basic-list__content']">
              해당 금리는 대출기간 36개월 기준이며 대출기간에 따라 금리가 변경될
              수 있습니다.
            </div>
          </li>
          <li :class="[$style['basic-list__item']]">
            <div :class="$style['basic-list__symbol']"></div>
            <div :class="$style['basic-list__content']">
              실제 정보와 입력 정보가 상이할 경우 대출가능금액 및 금리가 달라질
              수 있습니다.
            </div>
          </li>
        </ul>
      </div>

      <BasicHr
        theme="quaternary"
        type="contents"
        className="row-margin-container"
      />

      <div :class="$style['icon-list']">
        <ul :class="$style['icon-list__list']">
          <li :class="$style['icon-list__item']">
            <button type="button" :class="$style['icon-list__block']">
              <span :class="$style['icon-list__icon']"><IconCalculate /></span>
              <span :class="$style['icon-list__content']">
                <span :class="$style['icon-list__text']">월 납입금 계산</span>
                <span :class="$style['icon-list__title']">대출 계산기</span>
              </span>
            </button>
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
            <BasicButton>대출신청</BasicButton>
          </ButtonListItem>
        </ButtonList>
      </template>
    </FullPopup>
  </UiLayer>
</template>

<style lang="scss" module>
@import '@/assets/scss/views/personalLoan/LayerPersonalLoanETCCheck.scss';
</style>