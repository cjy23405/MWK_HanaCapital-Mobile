<script>
// My_M08_l001
import { ref } from 'vue';

import UiLayer from '@/components/ui/layer/UiLayer.vue';
import PopupTitle from '@/components/ui/layer/PopupTitle.vue';
import PopupButton from '@/components/ui/layer/PopupButton.vue';
import FullPopup from '@/components/ui/layer/FullPopup.vue';
import FullPopupHead from '@/components/ui/layer/FullPopupHead.vue';
import PageTextGroup from '@/components/ui/text/PageTextGroup.vue';
import PageMainText from '@/components/ui/text/PageMainText.vue';
import PageSubText from '@/components/ui/text/PageSubText.vue';
import BasicBox from '@/components/ui/common/BasicBox.vue';
import BasicBoxHead from '@/components/ui/common/BasicBoxHead.vue';
import BasicBoxHeadLeft from '@/components/ui/common/BasicBoxHeadLeft.vue';
import KeyValue from '@/components/ui/text/KeyValue.vue';
import KeyValueItem from '@/components/ui/text/KeyValueItem.vue';
import KeyValueTitle from '@/components/ui/text/KeyValueTitle.vue';
import KeyValueText from '@/components/ui/text/KeyValueText.vue';
import BasicHr from '@/components/ui/common/BasicHr.vue';
import ButtonList from '@/components/ui/button/ButtonList.vue';
import ButtonListItem from '@/components/ui/button/ButtonListItem.vue';
import BasicButton from '@/components/ui/button/BasicButton.vue';
import NoticeText from '@/components/ui/text/NoticeText.vue';
import UnitText from '@/components/ui/text/UnitText.vue';

import IconCustomer from '@/assets/images/icon/customer-center.svg?component';
import IconTell from '@/assets/images/icon/tell.svg?component';

export default {
  components: {
    UiLayer,
    PopupTitle,
    PopupButton,
    FullPopup,
    FullPopupHead,
    PageTextGroup,
    PageMainText,
    PageSubText,
    BasicBox,
    BasicBoxHead,
    BasicBoxHeadLeft,
    KeyValue,
    KeyValueItem,
    KeyValueTitle,
    KeyValueText,
    BasicHr,
    ButtonList,
    ButtonListItem,
    BasicButton,
    NoticeText,
    UnitText,
    IconCustomer,
    IconTell,
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
          <PopupTitle>만기안내장</PopupTitle>
          <template v-slot:right>
            <PopupButton @click="layerSlotProps.close()" />
          </template>
        </FullPopupHead>
      </template>

      <PageTextGroup>
        <PageMainText>만기안내장</PageMainText>
        <PageSubText>
          안녕하세요. 김하나님.<br />
          하나캐피탈을 이용해주신 손님께 깊은 감사를 드립니다.<br />
          <!-- Case : 리스일 경우 노출 -->
          손님께서 이용중인 오토리스의 만기가 다가오고 있습니다.
          <!--// Case : 리스일 경우 노출 -->
          <!-- Case : 렌트일 경우 노출 -->
          손님께서 이용중인 렌터카의 만기가 다가오고 있습니다.
          <!-- //Case : 렌트일 경우 노출 -->
        </PageSubText>
        <PageSubText>
          만기 1개월 전까지 만기상담 담당자가 배정되어, 만기 상담을 위하여 유선
          연락을 드릴 예정이오니, 상담원에게 만기처리방법(계약내용 참고) 중
          택일하여 알려주시면 구체적인 만기 절차를 안내해드리겠습니다.
        </PageSubText>
        <PageSubText>
          유선연락은 02-6911로 시작되는 번호로 상담이 진행되오니, 꼭 받아주시기
          바랍니다.
        </PageSubText>
        <PageSubText>
          개인/개인사업자 손님은 하나캐피탈 대표 App이용시 보다 편리하게
          거래정보확인, 만기처리 절차 및 만기처리방법을 직접 선택 가능합니다.
        </PageSubText>
        <NoticeText :classNames="{ wrap: 'row-margin-item' }">
          설치방법: 앱스토어 → “하나원큐캐피탈”검색 → 앱 설치
        </NoticeText>
      </PageTextGroup>

      <div>
        <BasicBox className="row-margin-item-group">
          <KeyValue>
            <KeyValueItem
              :classNames="{
                item: 'text-body-3',
              }"
            >
              <KeyValueTitle>만기일</KeyValueTitle>
              <KeyValueText>2023.01.01</KeyValueText>
            </KeyValueItem>
          </KeyValue>
        </BasicBox>

        <!-- Case : 리스일 경우 노출 -->
        <BasicBox className="row-margin-item-group">
          <BasicBoxHead>
            <BasicBoxHeadLeft>
              <h3 class="text-body-1 font-weight-medium">오토리스 20고5678</h3>
              <p class="text-body-4 color-gray row-margin-small">
                벤츠 더 뉴 C-class(W205/S205)
              </p>
            </BasicBoxHeadLeft>
          </BasicBoxHead>

          <KeyValue margin="regular">
            <KeyValueItem
              :classNames="{
                item: 'text-body-3',
              }"
            >
              <KeyValueTitle>리스 이용자</KeyValueTitle>
              <KeyValueText>김하나</KeyValueText>
            </KeyValueItem>

            <KeyValueItem
              :classNames="{
                item: 'text-body-3',
              }"
            >
              <KeyValueTitle>계약번호</KeyValueTitle>
              <KeyValueText>L1211000000000</KeyValueText>
            </KeyValueItem>

            <KeyValueItem
              :classNames="{
                item: 'text-body-3',
              }"
            >
              <KeyValueTitle>리스기간</KeyValueTitle>
              <KeyValueText>2개월</KeyValueText>
            </KeyValueItem>

            <KeyValueItem
              :classNames="{
                item: 'text-body-3',
              }"
            >
              <KeyValueTitle>계약기간</KeyValueTitle>
              <KeyValueText>2021.10.21 ~ 2021.12.05</KeyValueText>
            </KeyValueItem>

            <KeyValueItem
              :classNames="{
                item: 'text-body-3',
              }"
            >
              <KeyValueTitle>취득원가</KeyValueTitle>
              <KeyValueText>99,999,999 원</KeyValueText>
            </KeyValueItem>

            <KeyValueItem
              :classNames="{
                item: 'text-body-3',
              }"
            >
              <KeyValueTitle>리스보증금</KeyValueTitle>
              <KeyValueText>99,999,999 원</KeyValueText>
            </KeyValueItem>

            <KeyValueItem
              :classNames="{
                item: 'text-body-3',
              }"
            >
              <KeyValueTitle>잔존가치</KeyValueTitle>
              <KeyValueText>99,999,999 원</KeyValueText>
            </KeyValueItem>

            <KeyValueItem
              :classNames="{
                item: 'text-body-3',
              }"
            >
              <KeyValueTitle>만기처리방법</KeyValueTitle>
              <KeyValueText>연장/반환/구매</KeyValueText>
            </KeyValueItem>
          </KeyValue>
        </BasicBox>
        <!-- //Case : 리스일 경우 노출 -->

        <!-- Case : 렌트일 경우 노출 -->
        <BasicBox className="row-margin-item-group">
          <BasicBoxHead>
            <BasicBoxHeadLeft>
              <h3 class="text-body-1 font-weight-medium">렌터카 20고5678</h3>
              <p class="text-body-4 color-gray row-margin-small">
                벤츠 더 뉴 C-class(W205/S205)
              </p>
            </BasicBoxHeadLeft>
          </BasicBoxHead>

          <KeyValue margin="regular">
            <KeyValueItem
              :classNames="{
                item: 'text-body-3',
              }"
            >
              <KeyValueTitle>렌트 이용자</KeyValueTitle>
              <KeyValueText>김하나</KeyValueText>
            </KeyValueItem>

            <KeyValueItem
              :classNames="{
                item: 'text-body-3',
              }"
            >
              <KeyValueTitle>계약번호</KeyValueTitle>
              <KeyValueText>L1211000000000</KeyValueText>
            </KeyValueItem>

            <KeyValueItem
              :classNames="{
                item: 'text-body-3',
              }"
            >
              <KeyValueTitle>렌트기간</KeyValueTitle>
              <KeyValueText>2개월</KeyValueText>
            </KeyValueItem>

            <KeyValueItem
              :classNames="{
                item: 'text-body-3',
              }"
            >
              <KeyValueTitle>계약기간</KeyValueTitle>
              <KeyValueText>2021.10.21 ~ 2021.12.05</KeyValueText>
            </KeyValueItem>

            <KeyValueItem
              :classNames="{
                item: 'text-body-3',
              }"
            >
              <KeyValueTitle>취득원가</KeyValueTitle>
              <KeyValueText>99,999,999 원</KeyValueText>
            </KeyValueItem>

            <KeyValueItem
              :classNames="{
                item: 'text-body-3',
              }"
            >
              <KeyValueTitle>렌트보증금</KeyValueTitle>
              <KeyValueText>99,999,999 원</KeyValueText>
            </KeyValueItem>

            <KeyValueItem
              :classNames="{
                item: 'text-body-3',
              }"
            >
              <KeyValueTitle>잔존가치</KeyValueTitle>
              <KeyValueText>99,999,999 원</KeyValueText>
            </KeyValueItem>

            <KeyValueItem
              :classNames="{
                item: 'text-body-3',
              }"
            >
              <KeyValueTitle>만기처리방법</KeyValueTitle>
              <KeyValueText>연장/반환/구매</KeyValueText>
            </KeyValueItem>
          </KeyValue>
        </BasicBox>
        <!-- //Case : 렌트일 경우 노출 -->
      </div>

      <BasicHr className="row-margin-container-medium" />

      <div>
        <PageMainText>만기처리안내</PageMainText>
        <div class="row-margin-contents-group">
          <section class="row-margin-container-medium">
            <div class="row-margin-contents">
              <h4 class="text-title-2">연장</h4>
              <!-- Case : 리스일 경우 노출 -->
              <p
                class="text-body-4 color-gray row-margin-small font-weight-light"
              >
                차량의 잔존가치 9,999,999원으로 리스 기한 연장
              </p>
              <!-- //Case : 리스일 경우 노출 -->

              <!-- Case : 렌트일 경우 노출 -->
              <p
                class="text-body-4 color-gray row-margin-small font-weight-light"
              >
                차량의 잔존가치 9,999,999원으로 렌트 기한 연장
              </p>
              <!-- //Case : 렌트일 경우 노출 -->
            </div>

            <BasicBox>
              <KeyValue verticalAlign="center">
                <KeyValueItem
                  :classNames="{
                    item: 'text-body-1 font-weight-medium',
                  }"
                >
                  <KeyValueTitle
                    :classNames="{
                      title: 'color-black',
                    }"
                    >잔존가치
                  </KeyValueTitle>
                  <KeyValueText>
                    <UnitText
                      rightUnit="원"
                      align="right"
                      verticalAlign="center"
                    >
                      <strong>9,999,999</strong>
                    </UnitText>
                  </KeyValueText>
                </KeyValueItem>
              </KeyValue>
            </BasicBox>

            <!-- Case : 렌트일 경우 노출 -->
            <NoticeText :classNames="{ wrap: 'row-margin-item-group' }">
              단, 최초실행일로부터 60개월 이용 차량은 연장이 불가합니다.
            </NoticeText>
            <!-- //Case : 렌트일 경우 노출 -->
          </section>

          <section class="row-margin-container-medium">
            <h4 class="text-title-2 row-margin-contents">구매</h4>
            <!-- Case : 리스일 경우 노출 -->
            <BasicBox>
              <KeyValue verticalAlign="center">
                <KeyValueItem
                  :classNames="{
                    item: 'text-body-1 font-weight-medium',
                  }"
                >
                  <KeyValueTitle
                    :classNames="{
                      title: 'color-black',
                    }"
                    >구매대금
                  </KeyValueTitle>
                  <KeyValueText>
                    <UnitText
                      rightUnit="원"
                      align="right"
                      verticalAlign="center"
                    >
                      <strong>9,999,999</strong>
                    </UnitText>
                  </KeyValueText>
                </KeyValueItem>
              </KeyValue>
            </BasicBox>
            <div :class="[$style['contents-list'], 'row-margin-contents']">
              <ol
                :class="[
                  $style['contents-list__list'],
                  $style['contents-list__list--quinary'],
                ]"
              >
                <li :class="$style['contents-list__item']">
                  <div :class="$style['contents-list__head']">
                    <div :class="$style['contents-list__symbol']">1</div>
                    <div :class="$style['contents-list__title']">
                      구매대금은 별도로 납부하셔야 합니다.
                    </div>
                  </div>
                  <div
                    :class="[
                      $style['contents-list__depth-3'],
                      'row-margin-mini',
                    ]"
                  >
                    <p
                      class="text-body-4 font-weight-light color-gray-tertiary"
                    >
                      (리스 보증금이 있는 경우 차액분만 입금)
                    </p>
                  </div>
                </li>
                <li :class="$style['contents-list__item']">
                  <div :class="$style['contents-list__head']">
                    <div :class="$style['contents-list__symbol']">2</div>
                    <div :class="$style['contents-list__title']">
                      만기일 +10일 이내에 ‘차량등록명의’를 고객님으로 이전
                      완료(3자 이전금지) 하셔야 하며, 미이전 시에는
                      자동차관리법에 따른 범칙금이 부과됩니다.
                    </div>
                  </div>
                </li>
                <li :class="$style['contents-list__item']">
                  <div :class="$style['contents-list__head']">
                    <div :class="$style['contents-list__symbol']">3</div>
                    <div :class="$style['contents-list__title']">
                      명의 이전에 소요되는 각종 비용(등록세, 취득세, 공채비용
                      등)은 고객님 부담입니다.
                    </div>
                  </div>
                </li>
                <li :class="$style['contents-list__item']">
                  <div :class="$style['contents-list__head']">
                    <div :class="$style['contents-list__symbol']">4</div>
                    <div :class="$style['contents-list__title']">
                      소유권이전 등록은 손님이 직접 이전하는 방법과,
                      이전대행업체(주식회사 다코스)를 통한 이전 방법이 있습니다.
                      이전대행업체를 통한 이전 등록 시 이전대행비용이
                      발생됩니다.
                    </div>
                  </div>
                </li>
                <li :class="$style['contents-list__item']">
                  <div :class="$style['contents-list__head']">
                    <div :class="$style['contents-list__symbol']">5</div>
                    <div :class="$style['contents-list__title']">
                      『차량등록명의』가 이용자명의일 경우에도 차량 매입시
                      취득세가 발생합니다.
                    </div>
                  </div>
                </li>
              </ol>
            </div>
            <!-- //Case : 리스일 경우 노출 -->

            <!-- Case : 렌트일 경우 노출 -->
            <BasicBox>
              <KeyValue verticalAlign="center">
                <KeyValueItem
                  :classNames="{
                    item: 'text-body-1 font-weight-medium',
                  }"
                >
                  <KeyValueTitle
                    :classNames="{
                      title: 'color-black',
                    }"
                    >구매대금(VAT 포함)
                  </KeyValueTitle>
                  <KeyValueText>
                    <UnitText
                      rightUnit="원"
                      align="right"
                      verticalAlign="center"
                    >
                      <strong>9,999,999</strong>
                    </UnitText>
                  </KeyValueText>
                </KeyValueItem>
              </KeyValue>
            </BasicBox>
            <div :class="[$style['contents-list'], 'row-margin-contents']">
              <ol
                :class="[
                  $style['contents-list__list'],
                  $style['contents-list__list--quinary'],
                ]"
              >
                <li :class="$style['contents-list__item']">
                  <div :class="$style['contents-list__head']">
                    <div :class="$style['contents-list__symbol']">1</div>
                    <div :class="$style['contents-list__title']">
                      구매대금은 별도로 납부하셔야 합니다.
                    </div>
                  </div>
                  <div
                    :class="[
                      $style['contents-list__depth-3'],
                      'row-margin-mini',
                    ]"
                  >
                    <p
                      class="text-body-4 font-weight-light color-gray-tertiary"
                    >
                      (렌트 보증금이 있는 경우 차액분만 입금)
                    </p>
                  </div>
                </li>
                <li :class="$style['contents-list__item']">
                  <div :class="$style['contents-list__head']">
                    <div :class="$style['contents-list__symbol']">2</div>
                    <div :class="$style['contents-list__title']">
                      만기일 +10일 이내에 ‘차량등록명의’를 고객님으로 이전
                      완료(3자 이전금지) 하셔야 하며, 미이전 시에는
                      자동차관리법에 따른 범칙금이 부과됩니다.
                    </div>
                  </div>
                </li>
                <li :class="$style['contents-list__item']">
                  <div :class="$style['contents-list__head']">
                    <div :class="$style['contents-list__symbol']">3</div>
                    <div :class="$style['contents-list__title']">
                      명의 이전에 소요되는 각종 비용(등록세, 취득세, 공채비용
                      등)은 고객님 부담입니다.
                    </div>
                  </div>
                </li>
                <li :class="$style['contents-list__item']">
                  <div :class="$style['contents-list__head']">
                    <div :class="$style['contents-list__symbol']">4</div>
                    <div :class="$style['contents-list__title']">
                      소유권이전 등록은 손님이 직접 이전하는 방법과,
                      이전대행업체(주식회사 다코스)를 통한 이전 방법이 있습니다.
                      이전대행업체를 통한 이전 등록 시 이전대행비용이
                      발생됩니다.
                    </div>
                  </div>
                </li>
                <li :class="$style['contents-list__item']">
                  <div :class="$style['contents-list__head']">
                    <div :class="$style['contents-list__symbol']">5</div>
                    <div :class="$style['contents-list__title']">
                      렌터카 보험적용 가능기간: 렌터카만기일~14일
                    </div>
                  </div>
                  <div
                    :class="[
                      $style['contents-list__depth-3'],
                      'row-margin-mini',
                    ]"
                  >
                    <p
                      class="text-body-4 font-weight-light color-gray-tertiary"
                    >
                      (비영업일 포함/이후 보험적용 불가)
                    </p>
                    <ul :class="[$style['basic-list'], 'row-margin-mini']">
                      <li
                        :class="[
                          $style['basic-list__item'],
                          'text-body-4 color-black font-weight-regular',
                        ]"
                      >
                        <div :class="$style['basic-list__symbol']">-</div>
                        <div :class="$style['basic-list__content']">
                          렌터카 만기일 이후 고객명의 보험가입 필수<br />
                          (차대번호 가입)
                        </div>
                      </li>
                    </ul>
                  </div>
                </li>
              </ol>
            </div>
            <!-- //Case : 렌트일 경우 노출 -->
          </section>

          <section class="row-margin-container-medium">
            <div class="row-margin-contents">
              <h4 class="text-title-2">반환</h4>
              <p
                class="text-body-4 color-gray row-margin-small font-weight-light"
              >
                차량 반환 일시와 장소를 협의하여 반환 후 차량 평가
              </p>
            </div>
            <div :class="$style['contents-list']">
              <ol
                :class="[
                  $style['contents-list__list'],
                  $style['contents-list__list--quinary'],
                ]"
              >
                <li :class="$style['contents-list__item']">
                  <div :class="$style['contents-list__head']">
                    <div :class="$style['contents-list__symbol']">1</div>
                    <div :class="$style['contents-list__title']">
                      평가 결과에 따라 ‘차량평가정산금’이 발생될 수 있습니다.
                    </div>
                  </div>
                </li>
                <li :class="$style['contents-list__item']">
                  <div :class="$style['contents-list__head']">
                    <div :class="$style['contents-list__symbol']">2</div>
                    <div :class="$style['contents-list__title']">
                      차량 반환 지연 시에는 ‘반환지연금’이 추가로 부과됩니다.
                    </div>
                  </div>
                </li>
                <li :class="$style['contents-list__item']">
                  <div :class="$style['contents-list__head']">
                    <div :class="$style['contents-list__symbol']">3</div>
                    <div :class="$style['contents-list__title']">
                      반환 가능 여부 및 ‘차량평가정산금’에 관한 세부내용은
                      약관을 참조하시기 바랍니다.
                    </div>
                  </div>
                </li>
              </ol>
            </div>
          </section>

          <section class="row-margin-container-medium">
            <h4 class="text-title-2 row-margin-contents">공통사항</h4>
            <ul
              :class="[
                $style['basic-list'],
                $style['basic-list--regular-margin'],
              ]"
            >
              <li
                :class="[$style['basic-list__item'], 'text-body-3 color-black']"
              >
                <div :class="$style['basic-list__symbol']"></div>
                <div :class="$style['basic-list__content']">
                  만기 1개월전까지 담당자가 만기상담을 위해 연락드릴 예정입니다.
                </div>
              </li>
              <li
                :class="[$style['basic-list__item'], 'text-body-3 color-black']"
              >
                <div :class="$style['basic-list__symbol']"></div>
                <div :class="$style['basic-list__content']">
                  반환 또는 구매시점에는 확인되지 않은 범칙금, 과태료, 자동차세
                  등을 충당하기 위해 3개월간 예치하는 “해지후보증금”을
                  납부하셔야 합니다.
                </div>
              </li>
              <li
                :class="[$style['basic-list__item'], 'text-body-3 color-black']"
              >
                <div :class="$style['basic-list__symbol']"></div>
                <div :class="$style['basic-list__content']">
                  <div>승계(임차인변경)</div>
                  <ul :class="[$style['basic-list'], 'row-margin-item']">
                    <li
                      :class="[
                        $style['basic-list__item'],
                        'text-body-4 font-weight-regular color-black',
                      ]"
                    >
                      <div :class="$style['basic-list__symbol']">-</div>
                      <div :class="$style['basic-list__content']">
                        만기일로부터 2개월전 승계신청 원칙<br />
                        (만기일로부터 1개월전 승계불가)
                      </div>
                    </li>
                    <li
                      :class="[
                        $style['basic-list__item'],
                        'text-body-4 font-weight-regular color-red',
                      ]"
                    >
                      <div :class="$style['basic-list__symbol']">-</div>
                      <div :class="$style['basic-list__content']">
                        YY.MM.DD 이후에는 승계신청이 불가합니다.
                      </div>
                    </li>
                    <li
                      :class="[
                        $style['basic-list__item'],
                        'text-body-4 font-weight-regular color-black',
                      ]"
                    >
                      <div :class="$style['basic-list__symbol']">-</div>
                      <div :class="$style['basic-list__content']">
                        만기일로부터 3회차 이전 승계 접수 시 승계가능합니다.
                      </div>
                    </li>
                  </ul>
                </div>
              </li>
            </ul>
          </section>
        </div>
      </div>

      <BasicHr
        type="contents"
        theme="quaternary"
        className="row-margin-container"
      />

      <div :class="$style['icon-list']">
        <ul :class="$style['icon-list__list']">
          <!-- Case : 만기 6개월 전 일 때  노출 -->
          <li :class="$style['icon-list__item']">
            <div :class="$style['icon-list__block']">
              <div :class="$style['icon-list__icon']"><IconCustomer /></div>
              <div :class="$style['icon-list__content']">
                <div :class="$style['icon-list__title']">고객센터</div>
                <div :class="[$style['icon-list__text'], 'font-weight-light']">
                  평일 09:00 ~ 18:00
                </div>
              </div>
              <BasicButton
                tagName="a"
                size="mini"
                :line="true"
                theme="quaternary"
                :classNames="{ wrap: $style['icon-list__button'] }"
                href="tel:1800-1110"
              >
                <template v-slot:leftIcon><IconTell /></template>
                1800-1110
              </BasicButton>
            </div>
          </li>
          <!-- //Case : 만기 6개월 전 일 때  노출 -->

          <!-- Case : 만기 4개월 전 일 때  노출 -->
          <li :class="$style['icon-list__item']">
            <div :class="$style['icon-list__block']">
              <div :class="$style['icon-list__icon']"><IconCustomer /></div>
              <div :class="$style['icon-list__content']">
                <div :class="$style['icon-list__title']">만기상담</div>
                <div :class="[$style['icon-list__text'], 'font-weight-light']">
                  Fax 02-2037-3251
                </div>
              </div>
              <BasicButton
                tagName="a"
                size="mini"
                :line="true"
                theme="quaternary"
                :classNames="{ wrap: $style['icon-list__button'] }"
                href="tel:1800-9560"
              >
                <template v-slot:leftIcon><IconTell /></template>
                1800-9560
              </BasicButton>
            </div>
          </li>

          <!-- Case : 리스일 경우 노출 -->
          <li :class="$style['icon-list__item']">
            <div :class="$style['icon-list__block']">
              <div :class="$style['icon-list__icon']"><IconCustomer /></div>
              <div :class="$style['icon-list__content']">
                <div :class="$style['icon-list__title']">승계상담</div>
                <div :class="[$style['icon-list__text'], 'font-weight-light']">
                  Fax 02-2037-3207
                </div>
              </div>
              <BasicButton
                tagName="a"
                size="mini"
                :line="true"
                theme="quaternary"
                :classNames="{ wrap: $style['icon-list__button'] }"
                href="tel:02-3461-5538"
              >
                <template v-slot:leftIcon><IconTell /></template>
                02-3461-5538
              </BasicButton>
            </div>
          </li>
          <!-- //Case : 리스일 경우 노출 -->

          <!-- Case : 렌트일 경우 노출 -->
          <li :class="$style['icon-list__item']">
            <div :class="$style['icon-list__block']">
              <div :class="$style['icon-list__icon']"><IconCustomer /></div>
              <div :class="$style['icon-list__content']">
                <div :class="$style['icon-list__title']">승계상담</div>
                <div :class="[$style['icon-list__text'], 'font-weight-light']">
                  Fax 02-2037-3207
                </div>
              </div>
              <div>
                <BasicButton
                  tagName="a"
                  size="mini"
                  :line="true"
                  theme="quaternary"
                  :classNames="{ wrap: $style['icon-list__button'] }"
                  href="tel:02-3461-5538"
                >
                  <template v-slot:leftIcon><IconTell /></template>
                  02-3461-5538
                </BasicButton>
                <BasicButton
                  tagName="a"
                  size="mini"
                  :line="true"
                  theme="quaternary"
                  :classNames="{
                    wrap: [$style['icon-list__button'], 'row-margin-small'],
                  }"
                  href="tel:02-2037-4248"
                >
                  <template v-slot:leftIcon><IconTell /></template>
                  02-2037-4248
                </BasicButton>
              </div>
            </div>
          </li>
          <!-- //Case : 렌트일 경우 노출 -->
          <!-- //Case : 만기 4개월 전 일 때  노출 -->
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
@import '@/assets/scss/views/myLoan/LayerMyLoanMaturityNotice.scss';
</style>
