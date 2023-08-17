<script>
// Main_M01_p001
import { onMounted, onUnmounted } from 'vue';
import { RouterLink } from 'vue-router';
import { Pagination, A11y } from 'swiper';
import { Swiper, SwiperSlide } from 'swiper/vue';

import { useUiCommonStore } from '@/stores/ui/common';
import { useUiHeaderStore } from '@/stores/ui/header';

import PageContents from '@/components/ui/layout/PageContents.vue';
import PageTextGroup from '@/components/ui/text/PageTextGroup.vue';
import PageMainText from '@/components/ui/text/PageMainText.vue';
import UnitText from '@/components/ui/text/UnitText.vue';
import RoundStatus from '@/components/ui/text/RoundStatus.vue';
import BubbleProgress from '@/components/ui/progress/BubbleProgress.vue';
import TextButton from '@/components/ui/button/TextButton.vue';
import CarThumb from '@/components/ui/imageData/CarThumb.vue';
import BasicHr from '@/components/ui/common/BasicHr.vue';
import SlideBanner from '@/components/ui/banner/SlideBanner.vue';
import SlideBannerBlock from '@/components/ui/banner/SlideBannerBlock.vue';
import BasicButton from '@/components/ui/button/BasicButton.vue';
import BasicBannerSlide from '@/components/ui/banner/BasicBannerSlide.vue';
import BasicBanner from '@/components/ui/banner/BasicBanner.vue';

import IconAdd from '@/assets/images/icon/add.svg?component';
import IconLink from '@/assets/images/icon/link.svg?component';
import IconLinkSmall from '@/assets/images/icon/link-small.svg?component';
import IconDocumentSmall from '@/assets/images/icon/document-small.svg?component';
import IconBird from '@/assets/images/icon/bird.svg?component';
import IconGraph from '@/assets/images/icon/graph.svg?component';
import IconStudy from '@/assets/images/icon/study.svg?component';
import IconCapitalSmall from '@/assets/images/icon/img-capital-small.svg?component';

export default {
  components: {
    RouterLink,
    Swiper,
    SwiperSlide,
    PageContents,
    PageTextGroup,
    PageMainText,
    UnitText,
    RoundStatus,
    BubbleProgress,
    TextButton,
    CarThumb,
    BasicHr,
    SlideBanner,
    SlideBannerBlock,
    BasicButton,
    BasicBannerSlide,
    BasicBanner,
    IconAdd,
    IconLink,
    IconLinkSmall,
    IconDocumentSmall,
    IconBird,
    IconGraph,
    IconStudy,
    IconCapitalSmall,
  },
  setup() {
    const store = {
      ui: {
        common: useUiCommonStore(),
        header: useUiHeaderStore(),
      },
    };

    onMounted(() => {
      store.ui.common.setRootClassName('page-home');

      store.ui.header.setTitle(() => ' ');
      store.ui.header.setUseLeftLogo(() => true);
      store.ui.header.setUseAppButton(() => true);
    });

    onUnmounted(() => {
      store.ui.common.setRootClassName();

      store.ui.header.setTitle();
      store.ui.header.setUseLeftLogo();
      store.ui.header.setUseAppButton();
    });

    return {
      modules: [Pagination, A11y],
    };
  },
};
</script>

<template>
  <PageContents
    :classNames="{
      body: $style['web-body'],
    }"
  >
    <PageTextGroup>
      <PageMainText>
        <button type="button" :class="$style['top-link']">
          <strong>김하나님,</strong><br />
          오늘의 운세를 확인해 보세요!<IconLinkSmall
            :class="$style['top-link__icon']"
          />
        </button>
      </PageMainText>
    </PageTextGroup>

    <!-- Case : 진행 중인 상품 -->
    <section :class="$style['progress']">
      <div class="flex-box row-margin-contents">
        <div class="flex-box__cell">
          <div :class="$style['loan-icon']"></div>
        </div>
        <div class="flex-box__cell flex-box__cell--small flex-1">
          <h2 class="text-title-2">진행 중인 상품</h2>
        </div>
        <!-- Case : 다건일 경우 노출 -->
        <div class="flex-box__cell">
          <TextButton
            :block="true"
            :iconFillAll="true"
            :classNames="{
              wrap: 'text-body-4 color-gray',
            }"
          >
            전체보기
            <template v-slot:rightIcon>
              <IconAdd />
            </template>
          </TextButton>
        </div>
        <!-- // Case : 다건일 경우 노출 -->
      </div>

      <!-- Case : 신용대출 -->
      <div :class="$style['progress__block']">
        <div :class="$style['progress__head']">
          <div :class="$style['progress__head-left']">
            <div :class="$style['progress__head-row']">
              <h2 :class="$style['progress__title']">e하나신용대출</h2>
              <!-- Case : 다건일 경우 노출 -->
              <div :class="$style['progress__title-sub']">외 2건</div>
              <!-- // Case : 다건일 경우 노출 -->
            </div>
          </div>
          <div :class="$style['progress__head-right']">
            <p :class="$style['progress__date']">22.09.19 기준</p>
          </div>
        </div>

        <dl :class="$style['progress__info']">
          <div :class="$style['progress__info-item']">
            <dt :class="$style['progress__info-key']">최대한도</dt>
            <dd :class="$style['progress__info-val']">
              <UnitText
                rightUnit="만원"
                align="center"
                verticalAlign="center"
                size="medium"
                >7,000</UnitText
              >
            </dd>
          </div>
          <div :class="$style['progress__info-item']">
            <dt :class="$style['progress__info-key']">예상금리</dt>
            <dd :class="$style['progress__info-val']">
              <UnitText
                rightUnit="%"
                align="center"
                verticalAlign="center"
                size="medium"
                >5.2</UnitText
              >
            </dd>
          </div>
        </dl>

        <div :class="$style['progress__button']">
          <BasicButton size="small" :line="true">약정 이어하기</BasicButton>
        </div>
      </div>
      <!-- // Case : 신용대출 -->

      <!-- Case : 일반할부금융, 설비리스 -->
      <div :class="$style['progress__block']">
        <div :class="$style['progress__head']">
          <div :class="$style['progress__head-left']">
            <div :class="$style['progress__head-row']">
              <h2 :class="$style['progress__title']">의료기할부</h2>
              <!-- Case : 다건일 경우 노출 -->
              <div :class="$style['progress__title-sub']">외 2건</div>
              <!-- // Case : 다건일 경우 노출 -->
            </div>
          </div>
          <div :class="$style['progress__head-right']">
            <p :class="$style['progress__date']">22.09.19 기준</p>
          </div>
        </div>

        <dl :class="$style['progress__info']">
          <div :class="$style['progress__info-item']">
            <dt :class="$style['progress__info-key']">신청금액</dt>
            <dd :class="$style['progress__info-val']">
              <UnitText
                rightUnit="만원"
                align="center"
                verticalAlign="center"
                size="medium"
                >7,000</UnitText
              >
            </dd>
          </div>
          <div :class="$style['progress__info-item']">
            <dt :class="$style['progress__info-key']">금리</dt>
            <dd :class="$style['progress__info-val']">
              <UnitText
                rightUnit="%"
                align="center"
                verticalAlign="center"
                size="medium"
                >12.9</UnitText
              >
            </dd>
          </div>
        </dl>

        <div :class="$style['progress__button']">
          <BasicButton size="small" :line="true">약정 이어하기</BasicButton>
        </div>
      </div>
      <!-- // Case : 일반할부금융, 설비리스 -->

      <!-- Case : 자동차(리스/렌트 외) -->
      <div :class="$style['progress__block']">
        <div :class="$style['progress__head']">
          <div :class="$style['progress__head-left']">
            <div :class="$style['progress__head-row']">
              <h2 :class="$style['progress__title']">원큐다이렉트 오토론</h2>
              <!-- Case : 다건일 경우 노출 -->
              <div :class="$style['progress__title-sub']">외 2건</div>
              <!-- // Case : 다건일 경우 노출 -->
            </div>
          </div>
          <div :class="$style['progress__head-right']">
            <p :class="$style['progress__date']">22.09.19 기준</p>
          </div>
        </div>

        <dl :class="$style['progress__info']">
          <div :class="$style['progress__info-item']">
            <dt :class="$style['progress__info-key']">신청금액</dt>
            <dd :class="$style['progress__info-val']">
              <UnitText
                rightUnit="만원"
                align="center"
                verticalAlign="center"
                size="medium"
                >7,000</UnitText
              >
            </dd>
          </div>
        </dl>

        <div :class="$style['progress__button']">
          <BasicButton size="small" :line="true">약정 이어하기</BasicButton>
        </div>
      </div>
      <!-- // Case : 자동차(리스/렌트 외) -->

      <!-- Case : 리스/렌트 -->
      <div :class="$style['progress__block']">
        <div :class="$style['progress__head']">
          <div :class="$style['progress__head-left']">
            <div :class="$style['progress__head-row']">
              <h2 :class="$style['progress__title']">오토리스</h2>
              <!-- Case : 다건일 경우 노출 -->
              <div :class="$style['progress__title-sub']">외 2건</div>
              <!-- // Case : 다건일 경우 노출 -->
            </div>
          </div>
          <div :class="$style['progress__head-right']">
            <p :class="$style['progress__date']">22.09.19 기준</p>
          </div>
        </div>

        <dl :class="$style['progress__info']">
          <div :class="$style['progress__info-item']">
            <dt :class="$style['progress__info-key']">신청차량</dt>
            <dd :class="$style['progress__info-val']">
              <div :class="$style['progress__info-text']">제네시스 GV70</div>
            </dd>
          </div>
        </dl>

        <div :class="$style['progress__button']">
          <BasicButton size="small" :line="true">약정 이어하기</BasicButton>
        </div>
      </div>
      <!-- // Case : 리스/렌트 -->

      <div :class="$style['join']">
        <div :class="$style['join__inner']">
          <div :class="$style['join__icon']"><IconDocumentSmall /></div>
          <div :class="$style['join__title']">
            간편하게 서류를 등록해보세요.
          </div>
          <TextButton
            :block="true"
            :classNames="{
              wrap: [$style['join__link'], 'text-body-4 color-gray'],
            }"
          >
            서류등록
            <template v-slot:rightIcon>
              <IconLink />
            </template>
          </TextButton>
        </div>
      </div>
    </section>
    <!-- // Case : 진행 중인 상품 -->

    <!-- Case : 거래 상품 -->
    <section :class="$style['progress']">
      <div class="flex-box row-margin-contents">
        <div class="flex-box__cell">
          <div :class="$style['loan-icon']"></div>
        </div>
        <div class="flex-box__cell flex-box__cell--small flex-1">
          <h2 class="text-title-2">거래 상품</h2>
        </div>
        <!-- Case : 다건일 경우 노출 -->
        <div class="flex-box__cell">
          <TextButton
            :block="true"
            :iconFillAll="true"
            :classNames="{
              wrap: 'text-body-4 color-gray',
            }"
          >
            전체보기
            <template v-slot:rightIcon>
              <IconAdd />
            </template>
          </TextButton>
        </div>
        <!-- // Case : 다건일 경우 노출 -->
      </div>

      <div :class="$style['progress__block']">
        <div :class="[$style['progress__head'], 'align-items-start']">
          <div :class="$style['progress__head-left']">
            <div :class="$style['progress__head-row']">
              <h2 :class="$style['progress__title']">행복아파트론</h2>
              <!-- Case : 다건일 경우 노출 -->
              <div :class="$style['progress__title-sub']">외 2건</div>
              <!-- // Case : 다건일 경우 노출 -->
            </div>
          </div>
          <div :class="$style['progress__head-right']">
            <RoundStatus :classNames="{ wrap: 'display-block' }" theme="nonary">
              D-3
            </RoundStatus>
          </div>
        </div>

        <div :class="$style['progress__amount']">
          <dl :class="$style['progress__amount-block']">
            <!-- Case : 단건일 경우 노출 -->
            <dt :class="$style['progress__amount-key']">10.10 결제예정금액</dt>
            <!-- // Case : 단건일 경우 노출 -->

            <!-- Case : 다건일 경우 노출 -->
            <dt :class="$style['progress__amount-key']">이번달 총 결제금액</dt>
            <!-- // Case : 다건일 경우 노출 -->

            <dd :class="$style['progress__amount-val']">
              <UnitText
                rightUnit="원"
                align="center"
                verticalAlign="center"
                size="large"
                >400,000</UnitText
              >
            </dd>
          </dl>
          <!-- Case : 단건일 경우 노출 -->
          <div :class="$style['progress__amount-bar']">
            <BubbleProgress
              :total="12"
              :current="4"
              :label="
                (total, current) => {
                  return `총 ${total}회 중 ${current}회차`;
                }
              "
              :text="
                (total) => {
                  return `${total}회`;
                }
              "
              :bubble="
                (total, current) => {
                  return `${current}회차`;
                }
              "
            />
          </div>
          <!-- // Case : 단건일 경우 노출 -->
        </div>

        <!-- Case : 모든 상품(렌터카 외) -->
        <div :class="$style['progress__button']">
          <div :class="$style['buttons']">
            <div :class="$style['buttons__item']">
              <button type="button" :class="$style['button']">
                증명서 조회/발급
              </button>
            </div>
            <div :class="$style['buttons__hr']"></div>
            <div :class="$style['buttons__item']">
              <button type="button" :class="$style['button']">
                중도상환신청
              </button>
            </div>
          </div>
        </div>
        <!-- // Case : 모든 상품(렌터카 외) -->

        <!-- Case : 렌터카 -->
        <div :class="$style['progress__button']">
          <div :class="$style['buttons']">
            <div :class="$style['buttons__item']">
              <button type="button" :class="$style['button']">
                지정운전자
              </button>
            </div>
            <div :class="$style['buttons__hr']"></div>
            <div :class="$style['buttons__item']">
              <button type="button" :class="$style['button']">
                증명서 조회/발급
              </button>
            </div>
          </div>
        </div>
        <!-- // Case : 렌터카 -->

        <!-- Case : 스탁론 -->
        <div :class="$style['progress__button']">
          <div :class="$style['buttons']">
            <div :class="$style['buttons__item']">
              <button type="button" :class="$style['button']">연장하기</button>
            </div>
            <div :class="$style['buttons__hr']"></div>
            <div :class="$style['buttons__item']">
              <button type="button" :class="$style['button']">
                증명서 조회/발급
              </button>
            </div>
          </div>
        </div>
        <!-- // Case : 스탁론 -->

        <!-- Case : 렌터카, 오토리스(운용/금융) -->
        <div :class="$style['progress__button']">
          <div :class="$style['buttons']">
            <div :class="$style['buttons__item']">
              <button type="button" :class="$style['button']">
                만기후처리
              </button>
            </div>
            <div :class="$style['buttons__hr']"></div>
            <div :class="$style['buttons__item']">
              <button type="button" :class="$style['button']">
                근저당설정 조회/해지
              </button>
            </div>
          </div>
        </div>
        <!-- // Case : 렌터카, 오토리스(운용/금융) -->

        <!-- Case : 팩토링은 버튼 없음 -->
      </div>
    </section>
    <!-- // Case : 거래 상품 -->

    <div>
      <!-- 오토리스 / 렌터카 -->
      <section :class="$style['card']">
        <h2 :class="$style['card__title']">오토리스 / 렌터카</h2>
        <p :class="$style['card__text']">
          쉽고 빠른<br />
          렌터카 견적조회
        </p>
        <div :class="$style['card__image']">
          <img src="@/assets/images/contents/img-car.png" alt="" />
        </div>
        <div :class="[$style['buttons'], $style['buttons--auto']]">
          <div :class="$style['buttons__item']">
            <button type="button" :class="$style['button']">
              견적 바로가기
            </button>
          </div>
        </div>
      </section>
      <!-- // 오토리스 / 렌터카 -->

      <!-- 즉시출고 핫딜! -->
      <section class="row-margin-container-medium">
        <div class="flex-box row-margin-contents">
          <div class="flex-box__cell">
            <div :class="$style['hot-deal-icon']"></div>
          </div>
          <div class="flex-box__cell flex-box__cell--small flex-1">
            <h2 class="text-title-2">즉시출고 핫딜!</h2>
          </div>
          <div class="flex-box__cell">
            <TextButton
              :block="true"
              :iconFillAll="true"
              :classNames="{
                wrap: 'text-body-4 color-gray',
              }"
            >
              전체보기
              <template v-slot:rightIcon>
                <IconAdd />
              </template>
            </TextButton>
          </div>
        </div>
        <ul class="reset-list">
          <li v-for="i in 3" :key="i" class="row-margin-contents">
            <RouterLink to="" class="link-block">
              <span class="flex-box">
                <span class="flex-box__cell">
                  <CarThumb src="/images/_dummy/car-thumb.png" />
                </span>
                <span class="flex-box__cell flex-box__cell--medium flex-1">
                  <span class="display-block text-body-4 color-gray"
                    >현대 아이오닉6</span
                  >
                  <span class="display-block text-body-1 font-weight-medium"
                    >월 832,000 원</span
                  >
                </span>
                <span class="flex-box__cell flex-box__cell--medium">
                  <BasicButton size="mini" theme="quaternary" tagName="span">
                    옵션보기
                  </BasicButton>
                </span>
              </span>
            </RouterLink>
          </li>
        </ul>
      </section>
      <!-- // 즉시출고 핫딜! -->

      <!-- 중고차 오토론 -->
      <section
        :class="[
          $style['card'],
          $style['card--secondary'],
          'row-margin-contents',
        ]"
      >
        <h2 :class="$style['card__title']">중고차 오토론</h2>
        <p :class="$style['card__text']">
          중고차 구입<br />
          자금 대출
        </p>
        <div :class="$style['card__image']">
          <img src="@/assets/images/contents/img-used-car.png" alt="" />
        </div>
        <div :class="[$style['buttons'], $style['buttons--used-auto']]">
          <div :class="$style['buttons__item']">
            <button type="button" :class="$style['button']">
              상품 바로가기
            </button>
          </div>
        </div>
      </section>
      <!-- // 중고차 오토론 -->

      <!-- 신용대출 -->
      <section :class="[$style['card'], $style['card--tertiary']]">
        <h2 :class="$style['card__title']">신용대출</h2>
        <p :class="$style['card__text']">
          1분이면<br />
          한도조회 OK!
        </p>
        <div :class="$style['card__image']">
          <img src="@/assets/images/contents/img-document.png" alt="" />
        </div>
        <div :class="[$style['buttons'], $style['buttons--personal']]">
          <div :class="$style['buttons__item']">
            <button type="button" :class="$style['button']">한도조회</button>
          </div>
        </div>
      </section>
      <!-- // 신용대출 -->

      <div class="row-margin-item-group">
        <!-- 슬라이드 배너 A -->
        <!-- DD : 관리자 등록 배너 -->
        <SlideBanner>
          <Swiper :modules="modules" pagination>
            <!-- Case : 링크 기능 없을 때 -->
            <SwiperSlide>
              <SlideBannerBlock
                thumb="/images/_dummy/banner-003.png"
                :action="false"
              >
                <div class="text-body-1 font-weight-medium ellipsis">
                  높아진 한도 확인하세요!
                </div>
                <div
                  class="text-body-4 color-gray row-margin-mini multi-ellipsis"
                >
                  지금 신용조회하면 상품이 와르르
                </div>
              </SlideBannerBlock>
            </SwiperSlide>
            <!-- //Case : 링크 기능 없을 때 -->

            <!-- Case : 링크 기능 있을 때 (RouterLink) -->
            <SwiperSlide>
              <SlideBannerBlock
                thumb="/images/_dummy/banner-003.png"
                tagName="RouterLink"
                to=""
              >
                <div class="text-body-1 font-weight-medium ellipsis">
                  높아진 한도 확인하세요!
                </div>
                <div
                  class="text-body-4 color-gray row-margin-mini multi-ellipsis"
                >
                  지금 신용조회하면 상품이 와르르
                </div>
              </SlideBannerBlock>
            </SwiperSlide>
            <!-- // Case : 링크 기능 있을 때 -->

            <!-- Case : 링크 기능 있을 때 (a tag) -->
            <SwiperSlide>
              <SlideBannerBlock
                thumb="/images/_dummy/banner-003.png"
                tagName="a"
                href=""
              >
                <div class="text-body-1 font-weight-medium ellipsis">
                  높아진 한도 확인하세요!
                </div>
                <div
                  class="text-body-4 color-gray row-margin-mini multi-ellipsis"
                >
                  지금 신용조회하면 상품이 와르르
                </div>
              </SlideBannerBlock>
            </SwiperSlide>
            <!-- // Case : 링크 기능 있을 때 (a tag) -->
          </Swiper>
        </SlideBanner>
        <!-- // DD : 관리자 등록 배너 -->
        <!-- // 슬라이드 배너 A -->
      </div>
    </div>

    <BasicHr theme="secondary" :className="$style['hr']" />

    <div>
      <!-- 상품 배너 -->
      <div :class="$style['product']">
        <div :class="$style['product__contents']">
          <div :class="$style['product__group']">
            <RouterLink to="" :class="$style['product__block']">
              <div :class="$style['product__info']">
                <div :class="$style['product__sub']">의료기 · 설비</div>
                <div :class="$style['product__title']">리스</div>
              </div>
              <div :class="$style['product__image']">
                <img
                  src="@/assets/images/contents/img-medical-lease.png"
                  alt=""
                />
              </div>
            </RouterLink>
          </div>
          <div :class="$style['product__group']">
            <RouterLink to="" :class="$style['product__block']">
              <div :class="$style['product__info']">
                <div :class="$style['product__sub']">의료기 · 설비</div>
                <div :class="$style['product__title']">할부</div>
              </div>
              <div :class="$style['product__image']">
                <img
                  src="@/assets/images/contents/img-medical-installment.png"
                  alt=""
                />
              </div>
            </RouterLink>
          </div>
          <div
            :class="[$style['product__group'], $style['product__group--full']]"
          >
            <div
              :class="[
                $style['product__block'],
                $style['product__block--secondary'],
              ]"
            >
              <div :class="$style['product__item']">
                <RouterLink to="" :class="$style['product__link']">
                  <div :class="$style['product__info']">
                    <div :class="$style['product__sub']">#야나두 #가구</div>
                    <div :class="$style['product__title']">
                      생활 속 렌탈 상품
                    </div>
                  </div>
                  <div :class="$style['product__image']">
                    <img
                      src="@/assets/images/contents/img-main-rental.png"
                      alt=""
                    />
                  </div>
                </RouterLink>
              </div>
              <div :class="$style['product__item']">
                <RouterLink to="" :class="$style['product__link']">
                  <div :class="$style['product__info']">
                    <div :class="$style['product__sub']">한눈에 모아보는</div>
                    <div :class="$style['product__title']">다이렉트 보험</div>
                  </div>
                  <div :class="$style['product__image']">
                    <img
                      src="@/assets/images/contents/img-main-insurance.png"
                      alt=""
                    />
                  </div>
                </RouterLink>
              </div>
            </div>
          </div>
        </div>
      </div>
      <!-- // 상품 배너 -->

      <!-- 이런 서비스는 어때요? -->
      <section class="row-margin-container-medium">
        <h2 class="text-title-2 row-margin-contents">이런 서비스는 어때요?</h2>

        <div :class="$style['icon-list']">
          <ul :class="$style['icon-list__list']">
            <li :class="$style['icon-list__item']">
              <button type="button" :class="$style['icon-list__block']">
                <span
                  :class="[
                    $style['icon-list__icon'],
                    $style['icon-list__icon--white'],
                  ]"
                  ><IconBird
                /></span>
                <span :class="$style['icon-list__content']">
                  <span :class="$style['icon-list__text']"
                    >운새가 말해주는</span
                  >
                  <span :class="$style['icon-list__title']">오늘의 운세</span>
                </span>
              </button>
            </li>
            <li :class="$style['icon-list__item']">
              <button type="button" :class="$style['icon-list__block']">
                <span
                  :class="[
                    $style['icon-list__icon'],
                    $style['icon-list__icon--white'],
                  ]"
                  ><IconGraph
                /></span>
                <span :class="$style['icon-list__content']">
                  <span :class="$style['icon-list__text']"
                    >내 차, 저 아파트가 얼마일까?</span
                  >
                  <span :class="$style['icon-list__title']"
                    >아파트/자동차 시세조회</span
                  >
                </span>
              </button>
            </li>
            <li :class="$style['icon-list__item']">
              <button type="button" :class="$style['icon-list__block']">
                <span
                  :class="[
                    $style['icon-list__icon'],
                    $style['icon-list__icon--white'],
                  ]"
                  ><IconStudy
                /></span>
                <span :class="$style['icon-list__content']">
                  <span :class="$style['icon-list__text']"
                    >알아두면 유용한 재미있는 콘텐츠</span
                  >
                  <span :class="$style['icon-list__title']">스토리</span>
                </span>
              </button>
            </li>
          </ul>
        </div>
      </section>
      <!-- // 이런 서비스는 어때요? -->

      <div class="row-margin-container-medium">
        <!-- 슬라이드 배너 B -->
        <!-- DD : 관리자 등록 배너 -->
        <BasicBannerSlide>
          <Swiper :modules="modules" pagination>
            <!-- Case : 링크 기능 없을 때 -->
            <SwiperSlide>
              <BasicBanner
                :classNames="{ wrap: $style['bottom-banner'] }"
                thumb="/images/_dummy/banner-001.png"
                :action="false"
              >
                <p class="text-body-4 color-gray row-margin-mini ellipsis">
                  서브 텍스트 최대 한줄 노출 서브 텍스트 최대 한줄 노출
                </p>
                <h3 class="text-body-1 font-weight-medium ellipsis">
                  타이틀 텍스트 최대 한줄 노출 타이틀 텍스트 최대 한줄 노출
                </h3>
              </BasicBanner>
            </SwiperSlide>
            <!-- //Case : 링크 기능 없을 때 -->

            <!-- Case : 링크 기능 있을 때 (RouterLink) -->
            <SwiperSlide>
              <BasicBanner
                :classNames="{ wrap: $style['bottom-banner'] }"
                thumb="/images/_dummy/banner-001.png"
                tagName="RouterLink"
                to=""
              >
                <p class="text-body-4 color-gray row-margin-mini ellipsis">
                  서브 텍스트 최대 한줄 노출 서브 텍스트 최대 한줄 노출
                </p>
                <h3 class="text-body-1 font-weight-medium ellipsis">
                  타이틀 텍스트 최대 한줄 노출 타이틀 텍스트 최대 한줄 노출
                </h3>
              </BasicBanner>
            </SwiperSlide>
            <!-- // Case : 링크 기능 있을 때 -->

            <!-- Case : 링크 기능 있을 때 (a tag) -->
            <SwiperSlide>
              <BasicBanner
                :classNames="{ wrap: $style['bottom-banner'] }"
                thumb="/images/_dummy/banner-001.png"
                tagName="a"
                href=""
              >
                <p class="text-body-4 color-gray row-margin-mini ellipsis">
                  서브 텍스트 최대 한줄 노출 서브 텍스트 최대 한줄 노출
                </p>
                <h3 class="text-body-1 font-weight-medium ellipsis">
                  타이틀 텍스트 최대 한줄 노출 타이틀 텍스트 최대 한줄 노출
                </h3>
              </BasicBanner>
            </SwiperSlide>
            <!-- // Case : 링크 기능 있을 때 (a tag) -->
          </Swiper>
        </BasicBannerSlide>
        <!-- // DD : 관리자 등록 배너 -->
        <!-- // 슬라이드 배너 B -->
      </div>
    </div>

    <BasicHr theme="secondary" className="row-margin-container-medium" />

    <div>
      <!-- 공지 -->
      <section :class="$style['notice']">
        <h2 class="for-a11y">공지사항</h2>
        <RouterLink to="" :class="$style['notice__block']">
          <span :class="$style['notice__text']">
            채권양도 관련 개인신용정보 제공사실 공지문
          </span>
          <span :class="$style['notice__icon']">
            <IconLink />
          </span>
        </RouterLink>
      </section>
      <!-- // 공지 -->

      <!-- 앱 다운로드 안내 -->
      <section :class="$style['app']">
        <div :class="$style['app__icon']">
          <IconCapitalSmall />
        </div>
        <h2 :class="$style['app__title']">
          다양한 금융서비스 제공<br />
          <strong>쉽고 빠른 하나원큐 하나캐피탈!</strong>
        </h2>
        <div class="inline-wrap">
          <TextButton theme="secondary" :underline="true">
            앱 다운로드
          </TextButton>
        </div>
      </section>
      <!-- // 앱 다운로드 안내 -->
    </div>
  </PageContents>
</template>

<style lang="scss" module>
@import '@/assets/scss/views/main/MainHome.scss';
</style>