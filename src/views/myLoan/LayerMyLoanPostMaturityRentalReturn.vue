<script>
// My_M08_l010
import { ref } from 'vue';

import UiLayer from '@/components/ui/layer/UiLayer.vue';
import FullPopup from '@/components/ui/layer/FullPopup.vue';
import FullPopupHead from '@/components/ui/layer/FullPopupHead.vue';
import PopupTitle from '@/components/ui/layer/PopupTitle.vue';
import PopupButton from '@/components/ui/layer/PopupButton.vue';
import StepProgress from '@/components/ui/progress/StepProgress.vue';
import PageTextGroup from '@/components/ui/text/PageTextGroup.vue';
import PageMainText from '@/components/ui/text/PageMainText.vue';
import NoticeText from '@/components/ui/text/NoticeText.vue';
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
    StepProgress,
    PageTextGroup,
    PageMainText,
    NoticeText,
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
          <PopupTitle>만기후처리 반환</PopupTitle>
          <template v-slot:right>
            <PopupButton @click="layerSlotProps.close()" />
          </template>
        </FullPopupHead>
        <StepProgress :total="3" :current="1" />
      </template>

      <PageTextGroup>
        <PageMainText>
          반환 유의사항을<br />
          확인해 주세요
        </PageMainText>
      </PageTextGroup>

      <div>
        <section class="row-margin-contents-group">
          <h3 class="text-body-2 row-margin-item-medium">반환불가</h3>
          <p class="text-body-4 font-weight-light">
            당사는 불법개조, 침수, 화재 차량 등의 사유로 반환거부 혹은 취소할 수
            있습니다. (약관참고)
          </p>
        </section>

        <section class="row-margin-contents-group">
          <h3 class="text-body-2 row-margin-item-medium">차량 원상복구</h3>
          <p class="text-body-4 font-weight-light">
            차량의 손상도(생활기스, 깨짐, 긁힘 등)에 따라 원상복구비용이 발생될
            수 있으니, 반납 전 차량 원상복구가 필요합니다. 출고 후 설치하신 물품
            제거 및 개인물품 모두 확인 후 반납합니다. 차량키는 인수 시 수령하신
            키 모두 탁송 기사님께 차량과 함께 반납해 주세요.
          </p>
          <NoticeText :classNames="{ wrap: 'row-margin-item' }">
            수입차 : 사고로 인한 교체부분이 있을 경우 패널티가 발생 될 수
            있습니다.
          </NoticeText>
        </section>

        <section class="row-margin-contents-group">
          <h3 class="text-body-2 row-margin-item-medium">추가정산금</h3>
          <p class="text-body-4 font-weight-light">
            초과운행, 차량미반납으로 추가 정산금이 발생할 수 있습니다.
          </p>
          <NoticeText :classNames="{ wrap: 'row-margin-item' }">
            초과운행부담금 : 반납일까지 약정주행거리 초과시 1km당(국산차100원,
            수입렌터300원, 수입리스 250원)초과운행부담금 청구
          </NoticeText>
          <NoticeText>반환지연금 : 차량 반환 지연 시 부과</NoticeText>
        </section>

        <section class="row-margin-contents-group">
          <h3 class="text-body-2 row-margin-item-medium">반환약속 취소</h3>
          <p class="text-body-4 font-weight-light">
            반환일 당일 반환 취소시에는 추가금액이 발생될 수 있으니 일자, 장소
            등 변동사항은 반환일 이전 당사로 연락바랍니다.<br />
            (차량 반환 후 재출고 시 추가 비용이 발생됩니다.)
          </p>
        </section>

        <section class="row-margin-contents-group">
          <h3 class="text-body-2 row-margin-item-medium">자동차보험</h3>
          <p class="text-body-4 font-weight-light">
            차량 반납일 당일까지 보험을 유지해주세요.
          </p>
        </section>

        <section class="row-margin-contents-group">
          <h3 class="text-body-2 row-margin-item-medium">
            범칙금/과태료/제세공과금 납부
          </h3>
          <p class="text-body-4 font-weight-light">
            오토리스 이용 중 발생한 각종 제세공과금(자동차세, 과태료, 범칙금
            포함)등에 대해서는 본인의 책임하에 부담할 것을 확약합니다.
          </p>
        </section>
      </div>

      <template v-slot:foot>
        <ButtonList
          :classNames="{
            wrap: 'row-margin-none',
          }"
        >
          <ButtonListItem>
            <BasicButton>네, 모두 확인했습니다.</BasicButton>
          </ButtonListItem>
        </ButtonList>
      </template>
    </FullPopup>
  </UiLayer>
</template>
