<script>
import { ref } from 'vue';

import PageContents from '@/components/ui/layout/PageContents.vue';
import BasicButton from '@/components/ui/button/BasicButton.vue';
import ButtonList from '@/components/ui/button/ButtonList.vue';
import ButtonListItem from '@/components/ui/button/ButtonListItem.vue';

import LayerLeaseRentEstimationSystemSaveReviewCarNumber from '@/views/LeaseRentEstimationSystem/LayerLeaseRentEstimationSystemSaveReviewCarNumber.vue';
import LayerLeaseRentEstimationSystemSaveReviewDelivery from '@/views/LeaseRentEstimationSystem/LayerLeaseRentEstimationSystemSaveReviewDelivery.vue';
import LR_M04_b003 from '@/views/LeaseRentEstimationSystem/LR_M04_b003.vue';

export default {
  components: {
    PageContents,
    BasicButton,
    ButtonList,
    ButtonListItem,
    LayerLeaseRentEstimationSystemSaveReviewCarNumber,
    LayerLeaseRentEstimationSystemSaveReviewDelivery,
    LR_M04_b003,
  },
  setup() {
    const layer001 = ref(null);
    const layer002 = ref(null);
    const layer003 = ref(null);

    const layer001Open = (e = {}) => {
      layer001.value.layer.open(e.target);
    };
    const layer002Open = (e = {}) => {
      layer002.value.layer.open(e.target);
    };
    const layer003Open = (e = {}) => {
      layer003.value.layer.open(e.target);
    };

    return {
      layer001,
      layer002,
      layer003,
      layer001Open,
      layer002Open,
      layer003Open,
    };
  },
};
</script>

<template>
  <PageContents>
    <ButtonList
      :classNames="{
        wrap: 'row-margin-none',
      }"
      align="full"
    >
      <ButtonListItem>
        <BasicButton @click="layer001Open"
          >차량번호 등록 팝업<br />LR_M04_b001</BasicButton
        >
      </ButtonListItem>
      <ButtonListItem>
        <BasicButton @click="layer002Open"
          >인도요청 팝업<br />LR_M04_l001</BasicButton
        >
      </ButtonListItem>
      <ButtonListItem>
        <BasicButton @click="layer003Open"
          >심사신청 팝업<br />LR_M04_b003</BasicButton
        >
      </ButtonListItem>
    </ButtonList>

    <LayerLeaseRentEstimationSystemSaveReviewCarNumber ref="layer001" />
    <LayerLeaseRentEstimationSystemSaveReviewDelivery ref="layer002" />
    <LR_M04_b003 ref="layer003" />
  </PageContents>
</template>
