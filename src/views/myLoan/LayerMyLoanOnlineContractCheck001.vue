<script>
// My_M03_l005
// My_M03_b020
// My_M03_b023
// My_M03_b024
// My_M03_b025
// My_M03_b026
// My_M03_b027
// My_M03_b028
// My_M03_b029
// My_M03_b030
import { ref, reactive } from 'vue';

import UiLayer from '@/components/ui/layer/UiLayer.vue';
import PopupButton from '@/components/ui/layer/PopupButton.vue';
import FullPopup from '@/components/ui/layer/FullPopup.vue';
import FullPopupHead from '@/components/ui/layer/FullPopupHead.vue';
import PopupTitle from '@/components/ui/layer/PopupTitle.vue';
import PageTextGroup from '@/components/ui/text/PageTextGroup.vue';
import PageMainText from '@/components/ui/text/PageMainText.vue';
import PageSubText from '@/components/ui/text/PageSubText.vue';
import BasicButton from '@/components/ui/button/BasicButton.vue';
import ButtonList from '@/components/ui/button/ButtonList.vue';
import ButtonListItem from '@/components/ui/button/ButtonListItem.vue';
import StepProgress from '@/components/ui/progress/StepProgress.vue';
import BasicBox from '@/components/ui/common/BasicBox.vue';
import CheckBox from '@/components/ui/form/CheckBox.vue';
import CheckBoxLabelText from '@/components/ui/form/CheckBoxLabelText.vue';
import CheckBoxObject from '@/components/ui/form/CheckBoxObject.vue';
import BasicHr from '@/components/ui/common/BasicHr.vue';
import FormList from '@/components/ui/form/FormList.vue';
import FormListItem from '@/components/ui/form/FormListItem.vue';
import FormInvalid from '@/components/ui/form/FormInvalid.vue';
import FormInvalidMessage from '@/components/ui/form/FormInvalidMessage.vue';
import BasicInput from '@/components/ui/form/BasicInput.vue';
import BasicSelect from '@/components/ui/form/BasicSelect.vue';
import BoxCheck from '@/components/ui/form/BoxCheck.vue';
import BoxCheckLabel from '@/components/ui/form/BoxCheckLabel.vue';
import BoxCheckList from '@/components/ui/form/BoxCheckList.vue';
import BoxCheckListItem from '@/components/ui/form/BoxCheckListItem.vue';
import InputBlock from '@/components/ui/form/InputBlock.vue';
import InputBlockCell from '@/components/ui/form/InputBlockCell.vue';
import NoticeText from '@/components/ui/text/NoticeText.vue';

export default {
  components: {
    UiLayer,
    PopupButton,
    FullPopup,
    FullPopupHead,
    PopupTitle,
    PageTextGroup,
    PageMainText,
    PageSubText,
    BasicButton,
    ButtonList,
    ButtonListItem,
    StepProgress,
    BasicBox,
    CheckBox,
    CheckBoxLabelText,
    CheckBoxObject,
    BasicHr,
    FormList,
    FormListItem,
    FormInvalid,
    FormInvalidMessage,
    BasicInput,
    BasicSelect,
    BoxCheck,
    BoxCheckLabel,
    BoxCheckList,
    BoxCheckListItem,
    InputBlock,
    InputBlockCell,
    NoticeText,
  },
  setup() {
    const state = reactive({
      typeError: false,
      usageError: false,
      usageInputError: false,
      careerError: false,
      salesError: false,
      netProfitError: false,
      totalAssetsError: false,
      ageError: false,
      incomeError: false,
      assetError: false,
      expensesError: false,
      debtError: false,
      creditScoreError: false,
      liquidationError: false,
      creditRatingAgencyError: false,
      creditRatingError: false,
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
          <PopupTitle>온라인 약정</PopupTitle>
          <template v-slot:right>
            <PopupButton @click="layerSlotProps.close()" />
          </template>
        </FullPopupHead>
        <StepProgress :total="3" :current="2" />
      </template>

      <PageTextGroup
        :classNames="{
          wrap: 'row-margin-none',
        }"
      >
        <PageMainText>
          적합성.적정성 확인서의<br />
          체크리스트를 작성해 주세요
        </PageMainText>
        <PageSubText>
          본 확인서는 「금융소비자 보호에 관한 법률」에 의거하여 손님의
          재산상황, 금융상품 취득·처분 경험 등을 파악하여, 손님께서 신청하신
          상품이 손님의 상황에 적합·적정한지 여부를 확인하기 위해 활용됩니다.<br /><br />
          아래 체크리스트에 손님의 상황에 부합하거나 가장 가까운 항목을 정확히
          선택(체크표시(v)) 하여 주시기 바랍니다.
        </PageSubText>
      </PageTextGroup>

      <BasicHr className="row-margin-container-medium" />

      <section>
        <h2 class="text-title-2 row-margin-contents">체크리스트</h2>
        <FormList>
          <FormListItem titleText="전문금융소비자 해당여부" :forceFocus="true">
            <FormInvalid :error="state.typeError">
              <BoxCheckList>
                <BoxCheckListItem>
                  <BoxCheck
                    :minSide="true"
                    name="layerMyLoanOnlineContractCheck001_Customer"
                    id="layerMyLoanOnlineContractCheck001_Customer1"
                  >
                    <BoxCheckLabel>전문금융소비자</BoxCheckLabel>
                  </BoxCheck>
                </BoxCheckListItem>
                <BoxCheckListItem>
                  <BoxCheck
                    :minSide="true"
                    name="layerMyLoanOnlineContractCheck001_Customer"
                    id="layerMyLoanOnlineContractCheck001_Customer2"
                  >
                    <BoxCheckLabel>일반금융소비자</BoxCheckLabel>
                  </BoxCheck>
                </BoxCheckListItem>
              </BoxCheckList>
              <FormInvalidMessage>Error Message</FormInvalidMessage>
            </FormInvalid>
            <!-- Case : 전문금융소비자 선택시 노출 -->
            <NoticeText :classNames="{ wrap: 'row-margin-item' }">
              전문금융소비자 : 국가기관, 한국은행, 금융회사, 상시근로자 5인 이상
              법인·조합·단체, 대출모집인, SPC 등
            </NoticeText>
            <!-- //Case : 전문금융소비자 선택시 노출 -->
          </FormListItem>

          <FormListItem
            titleText="자금용도"
            target="#layerMyLoanOnlineContractCheck001_PurposeButton"
            :selectOnly="true"
          >
            <FormInvalid :error="state.usageError">
              <InputBlock :error="state.usageError">
                <InputBlockCell :flexible="true">
                  <BasicSelect
                    :option="[
                      {
                        value: '1',
                        text: '차량구입자금',
                      },
                      {
                        value: '2',
                        text: '주택자금',
                      },
                      {
                        value: '3',
                        text: '경조사금',
                      },
                      {
                        value: '4',
                        text: '타기관 대출금상환',
                      },
                      {
                        value: '5',
                        text: '교육비',
                      },
                      {
                        value: '6',
                        text: '의료비',
                      },
                      {
                        value: '7',
                        text: '가계자금',
                      },
                      {
                        value: '8',
                        text: '사업자금(운전자금)',
                      },
                      {
                        value: '9',
                        text: '기타',
                      },
                    ]"
                    buttonTitle="자금용도 선택하기"
                    layerTitle="자금용도를 선택해 주세요"
                    id="layerMyLoanOnlineContractCheck001_Purpose"
                    buttonId="layerMyLoanOnlineContractCheck001_PurposeButton"
                  />
                </InputBlockCell>
              </InputBlock>
              <FormInvalidMessage>Error Message</FormInvalidMessage>
            </FormInvalid>
          </FormListItem>

          <!-- Case : 자금용도 - '기타' 항목 선택 시 노출 -->
          <FormListItem
            titleText="자금용도 직접 입력"
            target="#layerMyLoanOnlineContractCheck001_PurposeInput"
          >
            <FormInvalid :error="state.usageInputError">
              <InputBlock :error="state.usageInputError">
                <InputBlockCell :flexible="true">
                  <BasicInput
                    title="자금용도"
                    id="layerMyLoanOnlineContractCheck001_PurposeInput"
                  />
                </InputBlockCell>
              </InputBlock>
              <FormInvalidMessage>Error Message</FormInvalidMessage>
            </FormInvalid>
          </FormListItem>
          <!-- //Case : 자금용도 - '기타' 항목 선택 시 노출 -->

          <!-- Case : 일반금융소비자 선택 시 노출 -->
          <FormListItem
            titleText="연령"
            target="#layerMyLoanOnlineContractCheck001_Age"
            :disabled="true"
          >
            <FormInvalid :error="state.ageError">
              <InputBlock :error="state.ageError" :disabled="true">
                <InputBlockCell :flexible="true">
                  <BasicInput
                    title="연령"
                    id="layerMyLoanOnlineContractCheck001_Age"
                    defaultValue="만 25세"
                    :disabled="true"
                  />
                </InputBlockCell>
              </InputBlock>
              <FormInvalidMessage>Error Message</FormInvalidMessage>
            </FormInvalid>
          </FormListItem>

          <FormListItem titleText="연간소득" :forceFocus="true">
            <FormInvalid :error="state.incomeError">
              <BoxCheckList align="full">
                <BoxCheckListItem>
                  <BoxCheck
                    :minSide="true"
                    name="layerMyLoanOnlineContractCheck001_Income"
                    id="layerMyLoanOnlineContractCheck001_Income1"
                  >
                    <BoxCheckLabel>5천만원 미만</BoxCheckLabel>
                  </BoxCheck>
                </BoxCheckListItem>
                <BoxCheckListItem>
                  <BoxCheck
                    :minSide="true"
                    name="layerMyLoanOnlineContractCheck001_Income"
                    id="layerMyLoanOnlineContractCheck001_Income2"
                  >
                    <BoxCheckLabel>5천만원 이상 ~ 1억원 미만</BoxCheckLabel>
                  </BoxCheck>
                </BoxCheckListItem>
                <BoxCheckListItem>
                  <BoxCheck
                    :minSide="true"
                    name="layerMyLoanOnlineContractCheck001_Income"
                    id="layerMyLoanOnlineContractCheck001_Income3"
                  >
                    <BoxCheckLabel>1억원 이상</BoxCheckLabel>
                  </BoxCheck>
                </BoxCheckListItem>
              </BoxCheckList>
              <FormInvalidMessage>Error Message</FormInvalidMessage>
            </FormInvalid>
          </FormListItem>

          <FormListItem titleText="보유자산" :forceFocus="true">
            <FormInvalid :error="state.assetError">
              <BoxCheckList align="full">
                <BoxCheckListItem>
                  <BoxCheck
                    :minSide="true"
                    name="layerMyLoanOnlineContractCheck001_Asset"
                    id="layerMyLoanOnlineContractCheck001_Asset1"
                  >
                    <BoxCheckLabel>1억원 미만</BoxCheckLabel>
                  </BoxCheck>
                </BoxCheckListItem>
                <BoxCheckListItem>
                  <BoxCheck
                    :minSide="true"
                    name="layerMyLoanOnlineContractCheck001_Asset"
                    id="layerMyLoanOnlineContractCheck001_Asset2"
                  >
                    <BoxCheckLabel>1억원 이상 ~ 10억원 미만</BoxCheckLabel>
                  </BoxCheck>
                </BoxCheckListItem>
                <BoxCheckListItem>
                  <BoxCheck
                    :minSide="true"
                    name="layerMyLoanOnlineContractCheck001_Asset"
                    id="layerMyLoanOnlineContractCheck001_Asset3"
                  >
                    <BoxCheckLabel>10억원 이상</BoxCheckLabel>
                  </BoxCheck>
                </BoxCheckListItem>
              </BoxCheckList>
              <FormInvalidMessage>Error Message</FormInvalidMessage>
            </FormInvalid>
          </FormListItem>
          <!-- //Case : 일반금융소비자 선택 시 노출 -->

          <!-- Case : 전문금융소비자 선택 시 노출 -->
          <FormListItem
            titleText="업력"
            target="#layerMyLoanOnlineContractCheck001_CareerPeriod"
          >
            <FormInvalid :error="state.careerError">
              <InputBlock :error="state.careerError">
                <InputBlockCell :flexible="true">
                  <BasicInput
                    align="right"
                    :useDelete="false"
                    pattern="\d*"
                    title="업력"
                    id="layerMyLoanOnlineContractCheck001_CareerPeriod"
                  />
                </InputBlockCell>
                <template v-slot:innerRight>
                  <div class="text-body-3">년</div>
                </template>
              </InputBlock>
              <FormInvalidMessage>Error Message</FormInvalidMessage>
            </FormInvalid>
          </FormListItem>
          <FormListItem
            titleText="매출액"
            target="#layerMyLoanOnlineContractCheck001_SalesButton"
            :selectOnly="true"
          >
            <FormInvalid :error="state.salesError">
              <InputBlock :error="state.salesError">
                <InputBlockCell :flexible="true">
                  <BasicSelect
                    :option="[
                      {
                        value: '1',
                        text: '항목 미정',
                      },
                    ]"
                    buttonTitle="매출액 선택하기"
                    layerTitle="매출액를 선택해 주세요"
                    id="layerMyLoanOnlineContractCheck001_Sales"
                    buttonId="layerMyLoanOnlineContractCheck001_SalesButton"
                  />
                </InputBlockCell>
              </InputBlock>
              <FormInvalidMessage>Error Message</FormInvalidMessage>
            </FormInvalid>
          </FormListItem>
          <FormListItem
            titleText="순이익 "
            target="#layerMyLoanOnlineContractCheck001_NetProfitButton"
            :selectOnly="true"
          >
            <FormInvalid :error="state.netProfitError">
              <InputBlock :error="state.netProfitError">
                <InputBlockCell :flexible="true">
                  <BasicSelect
                    :option="[
                      {
                        value: '1',
                        text: '항목 미정',
                      },
                    ]"
                    buttonTitle="순이익 선택하기"
                    layerTitle="순이익을 선택해 주세요"
                    id="layerMyLoanOnlineContractCheck001_NetProfit"
                    buttonId="layerMyLoanOnlineContractCheck001_NetProfitButton"
                  />
                </InputBlockCell>
              </InputBlock>
              <FormInvalidMessage>Error Message</FormInvalidMessage>
            </FormInvalid>
          </FormListItem>
          <FormListItem
            titleText="총자산 "
            target="#layerMyLoanOnlineContractCheck001_TotalAssetsButton"
            :selectOnly="true"
          >
            <FormInvalid :error="state.totalAssetsError">
              <InputBlock :error="state.totalAssetsError">
                <InputBlockCell :flexible="true">
                  <BasicSelect
                    :option="[
                      {
                        value: '1',
                        text: '항목 미정',
                      },
                    ]"
                    buttonTitle="총자산 선택하기"
                    layerTitle="총자산을 선택해 주세요"
                    id="layerMyLoanOnlineContractCheck001_TotalAssets"
                    buttonId="layerMyLoanOnlineContractCheck001_TotalAssetsButton"
                  />
                </InputBlockCell>
              </InputBlock>
              <FormInvalidMessage>Error Message</FormInvalidMessage>
            </FormInvalid>
          </FormListItem>
          <!--// Case : 전문금융소비자 선택 시 노출 -->

          <FormListItem
            titleText="고정지출"
            target="#layerMyLoanOnlineContractCheck001_FixedExpensesButton"
            :selectOnly="true"
          >
            <FormInvalid :error="state.expensesError">
              <InputBlock :error="state.expensesError">
                <InputBlockCell :flexible="true">
                  <BasicSelect
                    :option="[
                      {
                        value: '1',
                        text: '연간소득(매출)의 50% 미만',
                      },
                      {
                        value: '2',
                        text: '연간소득(매출)의 50% 이상 70% 미만',
                      },
                      {
                        value: '3',
                        text: '연간소득(매출)의 70% 이상 100% 미만',
                      },
                      {
                        value: '4',
                        text: '연간소득(매출)의 100% 이상',
                      },
                    ]"
                    buttonTitle="고정지출 선택하기"
                    layerTitle="고정지출을 선택해 주세요"
                    id="layerMyLoanOnlineContractCheck001_FixedExpenses"
                    buttonId="layerMyLoanOnlineContractCheck001_FixedExpensesButton"
                  />
                </InputBlockCell>
              </InputBlock>
              <FormInvalidMessage>Error Message</FormInvalidMessage>
            </FormInvalid>
          </FormListItem>

          <FormListItem titleText="부채" :forceFocus="true">
            <FormInvalid :error="state.debtError">
              <BoxCheckList align="full">
                <BoxCheckListItem>
                  <BoxCheck
                    :minSide="true"
                    name="layerMyLoanOnlineContractCheck001_Debt"
                    id="layerMyLoanOnlineContractCheck001_Debt1"
                  >
                    <BoxCheckLabel>5천만원 미만</BoxCheckLabel>
                  </BoxCheck>
                </BoxCheckListItem>
                <BoxCheckListItem>
                  <BoxCheck
                    :minSide="true"
                    name="layerMyLoanOnlineContractCheck001_Debt"
                    id="layerMyLoanOnlineContractCheck001_Debt2"
                  >
                    <BoxCheckLabel>5천만원 이상 ~ 5억원 미만</BoxCheckLabel>
                  </BoxCheck>
                </BoxCheckListItem>
                <BoxCheckListItem>
                  <BoxCheck
                    :minSide="true"
                    name="layerMyLoanOnlineContractCheck001_Debt"
                    id="layerMyLoanOnlineContractCheck001_Debt3"
                  >
                    <BoxCheckLabel>5억원 이상</BoxCheckLabel>
                  </BoxCheck>
                </BoxCheckListItem>
              </BoxCheckList>
              <FormInvalidMessage>Error Message</FormInvalidMessage>
            </FormInvalid>
          </FormListItem>

          <!-- Case : 일반금융소비자 선택 시 노출 -->
          <FormListItem
            titleText="신용점수"
            target="#layerMyLoanOnlineContractCheck001_CreditScore"
            :disabled="true"
          >
            <FormInvalid :error="state.creditScoreError">
              <InputBlock :error="state.creditScoreError" :disabled="true">
                <InputBlockCell :flexible="true">
                  <BasicInput
                    title="신용점수"
                    id="layerMyLoanOnlineContractCheck001_CreditScore"
                    defaultValue="756점 (평가사 : NICE신용평가)"
                    :disabled="true"
                  />
                </InputBlockCell>
              </InputBlock>
              <FormInvalidMessage>Error Message</FormInvalidMessage>
            </FormInvalid>
          </FormListItem>
          <!-- //Case : 일반금융소비자 선택 시 노출 -->

          <!-- Case : 전문금융소비자 선택 시 노출 -->
          <FormListItem
            titleText="신용평가사 "
            target="#layerMyLoanOnlineContractCheck001_CreditRatingAgencyButton"
            :selectOnly="true"
          >
            <FormInvalid :error="state.creditRatingAgencyError">
              <InputBlock :error="state.creditRatingAgencyError">
                <InputBlockCell :flexible="true">
                  <BasicSelect
                    :option="[
                      {
                        value: '1',
                        text: '항목 미정',
                      },
                    ]"
                    buttonTitle="신용평가사 선택하기"
                    layerTitle="신용평가사를 선택해 주세요"
                    id="layerMyLoanOnlineContractCheck001_CreditRatingAgency"
                    buttonId="layerMyLoanOnlineContractCheck001_CreditRatingAgencyButton"
                  />
                </InputBlockCell>
              </InputBlock>
              <FormInvalidMessage>Error Message</FormInvalidMessage>
            </FormInvalid>
          </FormListItem>
          <FormListItem
            titleText="신용등급"
            target="#layerMyLoanOnlineContractCheck001_CreditRatingButton"
            :selectOnly="true"
          >
            <FormInvalid :error="state.creditRatingError">
              <InputBlock :error="state.creditRatingError">
                <InputBlockCell :flexible="true">
                  <BasicSelect
                    :option="[
                      {
                        value: '1',
                        text: 'AAA',
                      },
                      {
                        value: '2',
                        text: 'AA+',
                      },
                      {
                        value: '3',
                        text: 'AA',
                      },
                      {
                        value: '4',
                        text: 'AA-',
                      },
                      {
                        value: '5',
                        text: 'A+',
                      },
                      {
                        value: '6',
                        text: 'A',
                      },
                      {
                        value: '7',
                        text: 'A-',
                      },
                    ]"
                    buttonTitle="신용등급 선택하기"
                    layerTitle="신용등급을 선택해 주세요"
                    id="layerMyLoanOnlineContractCheck001_CreditRating"
                    buttonId="layerMyLoanOnlineContractCheck001_CreditRatingButton"
                  />
                </InputBlockCell>
              </InputBlock>
              <FormInvalidMessage>Error Message</FormInvalidMessage>
            </FormInvalid>
          </FormListItem>
          <!-- //Case : 전문금융소비자 선택 시 노출 -->

          <FormListItem
            titleText="변제계획"
            target="#layerMyLoanOnlineContractCheck001_LiquidationButton"
            :selectOnly="true"
          >
            <FormInvalid :error="state.liquidationError">
              <InputBlock :error="state.liquidationError">
                <InputBlockCell :flexible="true">
                  <BasicSelect
                    :option="[
                      {
                        value: '1',
                        text: '매월 1일',
                      },
                      {
                        value: '2',
                        text: '매월 5일',
                      },
                      {
                        value: '3',
                        text: '매월 11일',
                      },
                      {
                        value: '4',
                        text: '매월 15일',
                      },
                      {
                        value: '5',
                        text: '매월 21일',
                      },
                    ]"
                    buttonTitle="변제계획 선택하기"
                    layerTitle="변제계획을 선택해 주세요"
                    id="layerMyLoanOnlineContractCheck001_Liquidation"
                    buttonId="layerMyLoanOnlineContractCheck001_LiquidationButton"
                  />
                </InputBlockCell>
              </InputBlock>
              <FormInvalidMessage>Error Message</FormInvalidMessage>
            </FormInvalid>
          </FormListItem>
        </FormList>
      </section>

      <section class="row-margin-container-medium">
        <h2 class="text-title-2 row-margin-contents">적합성·적정성 확인</h2>
        <BasicBox>
          <ol
            :class="[$style['basic-list'], $style['basic-list--normal-margin']]"
          >
            <li
              :class="[
                $style['basic-list__item'],
                'text-body-3',
                'color-gray-tertiary',
                'font-weight-regular',
              ]"
            >
              <div :class="$style['basic-list__symbol']">1.</div>
              <div :class="$style['basic-list__content']">
                당사에 제공한 적합성·적정성 관련 정보는 본인의 재산상황, 용도
                등의 정보를 정확히 알려드린 것입니다.
              </div>
            </li>
            <li
              :class="[
                $style['basic-list__item'],
                'text-body-3',
                'color-gray-tertiary',
                'font-weight-regular',
              ]"
            >
              <div :class="$style['basic-list__symbol']">2.</div>
              <div :class="$style['basic-list__content']">
                본인이 제공한 정보가 정확하지 않거나, 정보에 변경사항이 발생한
                경우에는 적합성·적정성 판단이 달라질 수 있음을 설명 받았습니다.
              </div>
            </li>
            <li
              :class="[
                $style['basic-list__item'],
                'text-body-3',
                'color-gray-tertiary',
                'font-weight-regular',
              ]"
            >
              <div :class="$style['basic-list__symbol']">3.</div>
              <div :class="$style['basic-list__content']">
                상기 목적을 위해 본인의 개인정보를 수집, 이용, 제공하는 것에
                동의합니다.
              </div>
            </li>
          </ol>
        </BasicBox>

        <CheckBox
          id="layerMyLoanCompatibilityAdequacyChk01"
          theme="tertiary"
          :classNames="{ wrap: 'row-margin-item-group' }"
        >
          <CheckBoxObject />
          <CheckBoxLabelText>
            본인은 당사에서 제공한 적합성·적정성 관련 정보와 관련하여 위 사항에
            동의합니다.
          </CheckBoxLabelText>
        </CheckBox>

        <div
          class="text-body-3 color-gray font-weight-light align-right row-margin-item-group"
        >
          2021.09.23
        </div>
        <div class="text-body-4 color-black align-right">
          신청인(또는 연대보증인) 김하나 (서명/인)
        </div>

        <BasicBox theme="senary" className="row-margin-contents-group">
          <div class="color-gray-secondary text-body-4">
            본 확인서는 [금융소비자 보호에 관한 법률] 제 17조 및 제 18조에 따라
            작성되었습니다.
          </div>
        </BasicBox>
      </section>

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
            <BasicButton>확인</BasicButton>
          </ButtonListItem>
        </ButtonList>
      </template>
    </FullPopup>
  </UiLayer>
</template>

<style lang="scss" module>
@import '@/assets/scss/views/myLoan/LayerMyLoanOnlineContractCheck.scss';
</style>
