<script>
// AF_M98_l003
import { ref } from 'vue';

import UiLayer from '@/components/ui/layer/UiLayer.vue';
import FullPopup from '@/components/ui/layer/FullPopup.vue';
import FullPopupHead from '@/components/ui/layer/FullPopupHead.vue';
import PopupButton from '@/components/ui/layer/PopupButton.vue';
import PopupTitle from '@/components/ui/layer/PopupTitle.vue';
import StepProgress from '@/components/ui/progress/StepProgress.vue';
import PageTextGroup from '@/components/ui/text/PageTextGroup.vue';
import PageMainText from '@/components/ui/text/PageMainText.vue';
import BasicBox from '@/components/ui/common/BasicBox.vue';
import BasicBoxHead from '@/components/ui/common/BasicBoxHead.vue';
import BasicBoxHeadLeft from '@/components/ui/common/BasicBoxHeadLeft.vue';
import KeyValue from '@/components/ui/text/KeyValue.vue';
import KeyValueItem from '@/components/ui/text/KeyValueItem.vue';
import KeyValueTitle from '@/components/ui/text/KeyValueTitle.vue';
import KeyValueText from '@/components/ui/text/KeyValueText.vue';
import ButtonList from '@/components/ui/button/ButtonList.vue';
import ButtonListItem from '@/components/ui/button/ButtonListItem.vue';
import BasicButton from '@/components/ui/button/BasicButton.vue';
import TextButton from '@/components/ui/button/TextButton.vue';
import NoticeText from '@/components/ui/text/NoticeText.vue';

import IconLink from '@/assets/images/icon/link.svg?component';
import IconCheckDocument from '@/assets/images/icon/check-document.svg?component';

export default {
  components: {
    UiLayer,
    FullPopup,
    FullPopupHead,
    PopupButton,
    PopupTitle,
    StepProgress,
    PageTextGroup,
    PageMainText,
    BasicBox,
    BasicBoxHead,
    BasicBoxHeadLeft,
    KeyValue,
    KeyValueItem,
    KeyValueTitle,
    KeyValueText,
    ButtonList,
    ButtonListItem,
    BasicButton,
    TextButton,
    NoticeText,
    IconLink,
    IconCheckDocument,
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
          <PopupTitle>온라인약정</PopupTitle>
          <template v-slot:right>
            <PopupButton @click="layerSlotProps.close()" />
          </template>
        </FullPopupHead>
        <StepProgress :total="8" :current="4" />
      </template>

      <PageTextGroup>
        <PageMainText>
          약정 정보를<br />
          확인해 주세요
        </PageMainText>
      </PageTextGroup>

      <div>
        <section class="row-margin-container-medium">
          <h3 class="text-title-2 row-margin-contents">대출 조건</h3>

          <BasicBox>
            <KeyValue margin="regular">
              <KeyValueItem
                :classNames="{
                  item: 'text-body-3',
                }"
              >
                <KeyValueTitle>상환방법</KeyValueTitle>
                <KeyValueText>원리금균등분할상환</KeyValueText>
              </KeyValueItem>
              <KeyValueItem
                :classNames="{
                  item: 'text-body-3',
                }"
              >
                <KeyValueTitle>대출기간</KeyValueTitle>
                <KeyValueText>24 개월</KeyValueText>
              </KeyValueItem>
              <KeyValueItem
                :classNames="{
                  item: 'text-body-3',
                }"
              >
                <KeyValueTitle>금리</KeyValueTitle>
                <KeyValueText>9.9 %</KeyValueText>
              </KeyValueItem>
              <KeyValueItem
                :classNames="{
                  item: 'text-body-3',
                }"
              >
                <KeyValueTitle>근저당 설정 비율</KeyValueTitle>
                <KeyValueText>10.0 %</KeyValueText>
              </KeyValueItem>
              <KeyValueItem
                :classNames="{
                  item: 'text-body-3',
                }"
              >
                <KeyValueTitle>근저당 설정 금액</KeyValueTitle>
                <KeyValueText>200,000 원</KeyValueText>
              </KeyValueItem>
              <KeyValueItem
                :classNames="{
                  item: 'text-body-3',
                }"
              >
                <KeyValueTitle>중도상환수수료</KeyValueTitle>
                <KeyValueText>
                  <div class="flex-box">
                    <div class="flex-box__cell flex-1">2%</div>
                    <div class="flex-box__cell">
                      <TextButton
                        :block="true"
                        underline="true"
                        theme="secondary"
                      >
                        수수료 산식
                      </TextButton>
                    </div>
                  </div>
                </KeyValueText>
              </KeyValueItem>
            </KeyValue>
            <NoticeText :classNames="{ wrap: 'color-red row-margin-item' }">
              대출기간별 수수료가 상이하며, 대출일로부터 3년 이내 상환 시 적용
            </NoticeText>
            <KeyValue
              margin="regular"
              :classNames="{ wrap: 'row-margin-item-group' }"
            >
              <KeyValueItem
                :classNames="{
                  item: 'text-body-3',
                }"
              >
                <KeyValueTitle>지연배상금</KeyValueTitle>
                <KeyValueText>12.9 %</KeyValueText>
              </KeyValueItem>
              <KeyValueItem
                :classNames="{
                  item: 'text-body-3',
                }"
              >
                <KeyValueTitle>초회 할부금</KeyValueTitle>
                <KeyValueText>68,010 원</KeyValueText>
              </KeyValueItem>
              <KeyValueItem
                :classNames="{
                  item: 'text-body-3',
                }"
              >
                <KeyValueTitle>월 할부금</KeyValueTitle>
                <KeyValueText>64,440 원</KeyValueText>
              </KeyValueItem>
              <KeyValueItem
                :classNames="{
                  item: 'text-body-3',
                }"
              >
                <KeyValueTitle>총 할부금</KeyValueTitle>
                <KeyValueText>2,323,410 원</KeyValueText>
              </KeyValueItem>
            </KeyValue>
          </BasicBox>
        </section>

        <section class="row-margin-container-medium">
          <h3 class="text-title-2 row-margin-contents">대출금 지급 안내</h3>

          <BasicBox>
            <KeyValue margin="regular">
              <KeyValueItem
                :classNames="{
                  item: 'text-body-3',
                }"
              >
                <KeyValueTitle>성명(상호)</KeyValueTitle>
                <KeyValueText>김하나</KeyValueText>
              </KeyValueItem>
              <KeyValueItem
                :classNames="{
                  item: 'text-body-3',
                }"
              >
                <KeyValueTitle>금융기관명</KeyValueTitle>
                <KeyValueText>하나은행</KeyValueText>
              </KeyValueItem>
              <KeyValueItem
                :classNames="{
                  item: 'text-body-3',
                }"
              >
                <KeyValueTitle>계좌번호</KeyValueTitle>
                <KeyValueText>****123123123123</KeyValueText>
              </KeyValueItem>
              <KeyValueItem
                :classNames="{
                  item: 'text-body-3',
                }"
              >
                <KeyValueTitle>위임지급금액</KeyValueTitle>
                <KeyValueText>24,990,000 원</KeyValueText>
              </KeyValueItem>
            </KeyValue>
          </BasicBox>

          <NoticeText :classNames="{ wrap: 'row-margin-item-group' }">
            매매계약서를 허위로 작성하거나 중고차 구매용도 이외에 다른 목적으로
            대출금을 신청하는 경우, 사문서 위조·사기 등으로 형사고발 조치 될 수
            있으니 주의해 주시기 바랍니다.
          </NoticeText>
        </section>

        <section class="row-margin-container-medium">
          <h3 class="text-title-2 row-margin-contents">
            자동차 근저당 설정계약서
          </h3>

          <div>
            <section class="row-margin-contents-group">
              <h4 class="text-body-2 row-margin-item-medium">
                채권자 겸 근저당권자
              </h4>

              <BasicBox>
                <KeyValue margin="regular">
                  <KeyValueItem
                    :classNames="{
                      item: 'text-body-3',
                    }"
                  >
                    <KeyValueTitle>주소</KeyValueTitle>
                    <KeyValueText>
                      88733<br />
                      인천 서구 청라1동 11, 청라동
                    </KeyValueText>
                  </KeyValueItem>
                  <KeyValueItem
                    :classNames="{
                      item: 'text-body-3',
                    }"
                  >
                    <KeyValueTitle>상호</KeyValueTitle>
                    <KeyValueText>하나캐피탈</KeyValueText>
                  </KeyValueItem>
                </KeyValue>
              </BasicBox>
            </section>

            <section class="row-margin-contents-group">
              <h4 class="text-body-2 row-margin-item-medium">
                근저당권 설정인
              </h4>

              <BasicBox>
                <KeyValue margin="regular">
                  <KeyValueItem
                    :classNames="{
                      item: 'text-body-3',
                    }"
                  >
                    <KeyValueTitle>주소</KeyValueTitle>
                    <KeyValueText>
                      88733<br />
                      인천 서구 청라1동 11, 청라동
                    </KeyValueText>
                  </KeyValueItem>
                  <KeyValueItem
                    :classNames="{
                      item: 'text-body-3',
                    }"
                  >
                    <KeyValueTitle>성명</KeyValueTitle>
                    <KeyValueText>김하나</KeyValueText>
                  </KeyValueItem>
                  <KeyValueItem
                    :classNames="{
                      item: 'text-body-3',
                    }"
                  >
                    <KeyValueTitle>생년월일</KeyValueTitle>
                    <KeyValueText>1998.01.23</KeyValueText>
                  </KeyValueItem>
                </KeyValue>
              </BasicBox>
            </section>

            <section class="row-margin-contents-group">
              <h4 class="text-body-2 row-margin-item-medium">채무자</h4>

              <BasicBox>
                <KeyValue margin="regular">
                  <KeyValueItem
                    :classNames="{
                      item: 'text-body-3',
                    }"
                  >
                    <KeyValueTitle>주소</KeyValueTitle>
                    <KeyValueText>
                      88733<br />
                      인천 서구 청라1동 11, 청라동
                    </KeyValueText>
                  </KeyValueItem>
                  <KeyValueItem
                    :classNames="{
                      item: 'text-body-3',
                    }"
                  >
                    <KeyValueTitle>성명</KeyValueTitle>
                    <KeyValueText>홍길동</KeyValueText>
                  </KeyValueItem>
                  <KeyValueItem
                    :classNames="{
                      item: 'text-body-3',
                    }"
                  >
                    <KeyValueTitle>생년월일</KeyValueTitle>
                    <KeyValueText>1998.01.23</KeyValueText>
                  </KeyValueItem>
                  <KeyValueItem
                    :classNames="{
                      item: 'text-body-3',
                    }"
                  >
                    <KeyValueTitle>
                      설정금액<br />
                      (채권가액)
                    </KeyValueTitle>
                    <KeyValueText>
                      금 100,000,000 원정<br />
                      (100,000,000 원)
                    </KeyValueText>
                  </KeyValueItem>
                </KeyValue>
              </BasicBox>
            </section>
          </div>
        </section>

        <section class="row-margin-container-medium">
          <h3 class="text-title-2 row-margin-contents">자동차의 표시</h3>

          <BasicBox className="row-margin-item-group">
            <BasicBoxHead>
              <BasicBoxHeadLeft>
                <p class="text-body-4 font-weight-light row-margin-mini">
                  2020년식
                </p>

                <h3 class="text-body-1 font-weight-medium">123가1234</h3>
                <p class="text-body-4 color-gray row-margin-small">
                  올 뉴 아반떼/인스퍼레이션
                </p>
              </BasicBoxHeadLeft>
            </BasicBoxHead>

            <KeyValue>
              <KeyValueItem
                :classNames="{
                  item: 'text-body-3',
                }"
              >
                <KeyValueTitle>차대번호</KeyValueTitle>
                <KeyValueText>ASDFSD1231ASDF</KeyValueText>
              </KeyValueItem>
            </KeyValue>
          </BasicBox>
        </section>

        <section class="row-margin-container-medium">
          <div class="flex-box row-margin-contents">
            <div class="flex-box__cell">
              <h3 class="text-title-2">파일업로드</h3>
            </div>
            <div class="flex-box__cell flex-box__cell--small">
              <div class="text-body-3">(필수)</div>
            </div>
          </div>

          <!-- Case : : 등록 전 -->
          <button
            type="button"
            :class="[$style['add-button'], 'row-margin-item']"
          >
            <span :class="$style['add-button__inner']">
              <span :class="$style['add-button__text']">서류등록</span>
              <span
                :class="[
                  $style['add-button__icon'],
                  $style['add-button__icon--secondary'],
                ]"
              >
                <IconLink />
              </span>
            </span>
          </button>
          <!-- //Case : : 등록 전 -->

          <!-- Case : : 등록 후 -->
          <BasicBox>
            <div class="flex-box">
              <div class="flex-box__cell">
                <IconCheckDocument class="display-block" />
              </div>
              <div class="flex-box__cell flex-1">
                <div class="text-body-3">등록 완료</div>
              </div>
              <div class="flex-box__cell">
                <BasicButton size="mini" theme="quaternary">
                  추가첨부
                </BasicButton>
              </div>
            </div>
          </BasicBox>
          <!-- //Case : : 등록 후 -->
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
            <BasicButton>약정하기</BasicButton>
          </ButtonListItem>
        </ButtonList>
      </template>
    </FullPopup>
  </UiLayer>
</template>

<style lang="scss" module>
@import '@/assets/scss/views/myLoan/LayerMyLoanOnlineContractUsedLoanFinalConfirm001.scss';
</style>
