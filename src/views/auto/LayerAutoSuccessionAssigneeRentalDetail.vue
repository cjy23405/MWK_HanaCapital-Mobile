<script>
// AF_M07_b004
import { ref } from 'vue';

import UiLayer from '@/components/ui/layer/UiLayer.vue';
import ToastPopup from '@/components/ui/layer/ToastPopup.vue';
import ToastPopupHead from '@/components/ui/layer/ToastPopupHead.vue';
import PopupTitle from '@/components/ui/layer/PopupTitle.vue';
import KeyValue from '@/components/ui/text/KeyValue.vue';
import KeyValueItem from '@/components/ui/text/KeyValueItem.vue';
import KeyValueTitle from '@/components/ui/text/KeyValueTitle.vue';
import KeyValueText from '@/components/ui/text/KeyValueText.vue';
import BasicButton from '@/components/ui/button/BasicButton.vue';
import ButtonList from '@/components/ui/button/ButtonList.vue';
import ButtonListItem from '@/components/ui/button/ButtonListItem.vue';
import BasicTooltip from '@/components/ui/tooltip/BasicTooltip.vue';
import BasicHr from '@/components/ui/common/BasicHr.vue';

import IconTooltip from '@/assets/images/icon/tooltip.svg?component';

export default {
  components: {
    UiLayer,
    ToastPopup,
    ToastPopupHead,
    PopupTitle,
    KeyValue,
    KeyValueItem,
    KeyValueTitle,
    KeyValueText,
    BasicButton,
    ButtonList,
    ButtonListItem,
    BasicTooltip,
    BasicHr,
    IconTooltip,
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
  <UiLayer ref="layer" type="toast" :backgroundClose="true">
    <ToastPopup>
      <template v-slot:head>
        <ToastPopupHead>
          <PopupTitle>렌트 상세조건</PopupTitle>
        </ToastPopupHead>
      </template>

      <KeyValue margin="regular">
        <KeyValueItem>
          <KeyValueTitle>
            <div class="flex-box">
              <div class="flex-box__cell">렌트료 합계</div>
              <div class="flex-box__cell flex-box__cell--small">
                <BasicTooltip placement="bottom">
                  <IconTooltip :class="$style['icon']" />
                  <span class="for-a11y">(도움말)</span>

                  <template v-slot:contents>
                    <section :class="$style['tooltip-section']">
                      <h3 :class="$style['tooltip-section__title']">
                        렌트료 합계
                      </h3>
                      <p :class="$style['tooltip-section__text']">
                        “잔여기간(00개월)×월 렌트료(0원)”으로 렌트료 총 납부금액
                        0원입니다.
                      </p>
                    </section>
                  </template>
                </BasicTooltip>
              </div>
            </div>
          </KeyValueTitle>
          <KeyValueText>
            <div>0 원</div>
            <div
              class="text-body-4 font-weight-light color-gray-tertiary row-margin-mini"
            >
              자동차세 포함
            </div>
          </KeyValueText>
        </KeyValueItem>

        <KeyValueItem>
          <KeyValueTitle>
            <div class="flex-box">
              <div class="flex-box__cell">만기 인수 시 납부금액</div>
              <div class="flex-box__cell flex-box__cell--small">
                <BasicTooltip placement="bottom">
                  <IconTooltip :class="$style['icon']" />
                  <span class="for-a11y">(도움말)</span>

                  <template v-slot:contents>
                    <section :class="$style['tooltip-section']">
                      <h3 :class="$style['tooltip-section__title']">
                        만기 인수 시 납부금액
                      </h3>
                      <p :class="$style['tooltip-section__text']">
                        “잔존가치(0원)-보증금(0원)”으로 0원 납부하시면 인수
                        가능합니다.
                      </p>
                    </section>
                  </template>
                </BasicTooltip>
              </div>
            </div>
          </KeyValueTitle>
          <KeyValueText>0 원</KeyValueText>
        </KeyValueItem>

        <KeyValueItem>
          <KeyValueTitle>만기 반환 시 환급금액</KeyValueTitle>
          <KeyValueText>0 원</KeyValueText>
        </KeyValueItem>

        <KeyValueItem>
          <KeyValueTitle>승계수수료</KeyValueTitle>
          <KeyValueText>5,000,000 원</KeyValueText>
        </KeyValueItem>
      </KeyValue>

      <BasicHr
        theme="quaternary"
        type="contents"
        className="row-margin-contents-small"
      />

      <KeyValue margin="regular">
        <KeyValueItem>
          <KeyValueTitle>
            <div class="flex-box">
              <div class="flex-box__cell">보증금</div>
              <div class="flex-box__cell flex-box__cell--small">
                <BasicTooltip>
                  <IconTooltip :class="$style['icon']" />
                  <span class="for-a11y">(도움말)</span>

                  <template v-slot:contents>
                    <section :class="$style['tooltip-section']">
                      <h3 :class="$style['tooltip-section__title']">보증금</h3>
                      <p :class="$style['tooltip-section__text']">
                        렌트사에 예치해 놓은 금액(반환 시 환급)
                      </p>
                    </section>
                  </template>
                </BasicTooltip>
              </div>
            </div>
          </KeyValueTitle>
          <KeyValueText>0 원</KeyValueText>
        </KeyValueItem>

        <KeyValueItem>
          <KeyValueTitle>
            <div class="flex-box">
              <div class="flex-box__cell">잔여선납금</div>
              <div class="flex-box__cell flex-box__cell--small">
                <BasicTooltip>
                  <IconTooltip :class="$style['icon']" />
                  <span class="for-a11y">(도움말)</span>

                  <template v-slot:contents>
                    <section :class="$style['tooltip-section']">
                      <h3 :class="$style['tooltip-section__title']">
                        잔여선납금
                      </h3>
                      <p :class="$style['tooltip-section__text']">
                        잔여기간으로 나누어 매월 렌트료에 충당
                      </p>
                    </section>
                  </template>
                </BasicTooltip>
              </div>
            </div>
          </KeyValueTitle>
          <KeyValueText>0 원</KeyValueText>
        </KeyValueItem>

        <KeyValueItem>
          <KeyValueTitle>
            <div class="flex-box">
              <div class="flex-box__cell">잔존가치 (VAT포함)</div>
              <div class="flex-box__cell flex-box__cell--small">
                <BasicTooltip>
                  <IconTooltip :class="$style['icon']" />
                  <span class="for-a11y">(도움말)</span>

                  <template v-slot:contents>
                    <section :class="$style['tooltip-section']">
                      <h3 :class="$style['tooltip-section__title']">
                        잔여선납금
                      </h3>
                      <p :class="$style['tooltip-section__text']">
                        만기 시 차량 인수를 위해 납입해야하는 비용
                      </p>
                    </section>
                  </template>
                </BasicTooltip>
              </div>
            </div>
          </KeyValueTitle>
          <KeyValueText>0 원</KeyValueText>
        </KeyValueItem>

        <KeyValueItem>
          <KeyValueTitle>
            <div class="flex-box">
              <div class="flex-box__cell">월 렌트료</div>
              <div class="flex-box__cell flex-box__cell--small">
                <BasicTooltip>
                  <IconTooltip :class="$style['icon']" />
                  <span class="for-a11y">(도움말)</span>

                  <template v-slot:contents>
                    <section :class="$style['tooltip-section']">
                      <h3 :class="$style['tooltip-section__title']">
                        월 렌트료
                      </h3>
                      <p :class="$style['tooltip-section__text']">
                        매월 렌트사에 납부해야하는 금액
                      </p>
                    </section>
                  </template>
                </BasicTooltip>
              </div>
            </div>
          </KeyValueTitle>
          <KeyValueText>0 원</KeyValueText>
        </KeyValueItem>

        <KeyValueItem>
          <KeyValueTitle>렌트기간</KeyValueTitle>
          <KeyValueText>00개월</KeyValueText>
        </KeyValueItem>

        <KeyValueItem>
          <KeyValueTitle>계약주행거리</KeyValueTitle>
          <KeyValueText>100,000Km</KeyValueText>
        </KeyValueItem>

        <KeyValueItem>
          <KeyValueTitle>종료 후 처리</KeyValueTitle>
          <KeyValueText>-</KeyValueText>
        </KeyValueItem>

        <KeyValueItem>
          <KeyValueTitle>
            렌트 만기일자 /<br />
            최종결제일자
          </KeyValueTitle>
          <KeyValueText>
            2023.04.01 /<br />
            2023.09.11
          </KeyValueText>
        </KeyValueItem>

        <KeyValueItem>
          <KeyValueTitle>정비 서비스</KeyValueTitle>
          <KeyValueText>-</KeyValueText>
        </KeyValueItem>

        <KeyValueItem>
          <KeyValueTitle>보험가입정보</KeyValueTitle>
          <KeyValueText>-</KeyValueText>
        </KeyValueItem>
      </KeyValue>

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
    </ToastPopup>
  </UiLayer>
</template>

<style lang="scss" module>
@import '@/assets/scss/views/auto/LayerAutoSuccessionAssigneeRentalDetail.scss';
</style>
