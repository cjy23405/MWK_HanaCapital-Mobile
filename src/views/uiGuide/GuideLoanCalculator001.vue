<script>
import { ref } from 'vue';

import PageContents from '@/components/ui/layout/PageContents.vue';
import BasicButton from '@/components/ui/button/BasicButton.vue';
import ButtonList from '@/components/ui/button/ButtonList.vue';
import ButtonListItem from '@/components/ui/button/ButtonListItem.vue';

import LayerLoanCalculator from '@/views/loanCalculator/LayerLoanCalculator.vue';
import LayerLoanCalculatorResult from '@/views/loanCalculator/LayerLoanCalculatorResult.vue';

export default {
  components: {
    PageContents,
    BasicButton,
    ButtonList,
    ButtonListItem,
    LayerLoanCalculator,
    LayerLoanCalculatorResult,
  },
  setup() {
    const layer001 = ref(null);
    const layer002 = ref(null);

    const layer001Open = (e = {}) => {
      layer001.value.layer.open(e.target);
    };
    const layer002Open = (e = {}) => {
      layer002.value.layer.open(e.target);
    };

    return {
      layer001,
      layer002,
      layer001Open,
      layer002Open,
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
        <BasicButton @click="layer001Open">
          대출계산기<br />Common_M00_l016
        </BasicButton>
      </ButtonListItem>
      <ButtonListItem>
        <BasicButton @click="layer002Open">
          대출계산기 결과<br />Common_M00_b014
        </BasicButton>
      </ButtonListItem>
    </ButtonList>

    <LayerLoanCalculator ref="layer001" />
    <LayerLoanCalculatorResult ref="layer002" />
  </PageContents>
</template>
