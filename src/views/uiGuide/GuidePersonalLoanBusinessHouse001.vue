<script>
import { ref } from 'vue';

import PageContents from '@/components/ui/layout/PageContents.vue';
import BasicButton from '@/components/ui/button/BasicButton.vue';
import ButtonList from '@/components/ui/button/ButtonList.vue';
import ButtonListItem from '@/components/ui/button/ButtonListItem.vue';

import LayerPersonalLoanIdentificationMethodSelect from '@/views/personalLoan/LayerPersonalLoanIdentificationMethodSelect.vue';
import LayerPersonalLoanBusinessHouseAgree from '@/views/personalLoan/LayerPersonalLoanBusinessHouseAgree.vue';
import LayerPersonalLoanBusinessHouseNotice from '@/views/personalLoan/LayerPersonalLoanBusinessHouseNotice.vue';
import LayerPersonalLoanBusinessHouseForm from '@/views/personalLoan/LayerPersonalLoanBusinessHouseForm.vue';
import LayerPersonalLoanBusinessHouseComplete from '@/views/personalLoan/LayerPersonalLoanBusinessHouseComplete.vue';

export default {
  components: {
    PageContents,
    BasicButton,
    ButtonList,
    ButtonListItem,
    LayerPersonalLoanIdentificationMethodSelect,
    LayerPersonalLoanBusinessHouseAgree,
    LayerPersonalLoanBusinessHouseNotice,
    LayerPersonalLoanBusinessHouseForm,
    LayerPersonalLoanBusinessHouseComplete,
  },
  setup() {
    const layer001 = ref(null);
    const layer002 = ref(null);
    const layer003 = ref(null);
    const layer004 = ref(null);
    const layer005 = ref(null);

    const layer001Open = (e = {}) => {
      layer001.value.layer.open(e.target);
    };
    const layer002Open = (e = {}) => {
      layer002.value.layer.open(e.target);
    };
    const layer003Open = (e = {}) => {
      layer003.value.layer.open(e.target);
    };
    const layer004Open = (e = {}) => {
      layer004.value.layer.open(e.target);
    };
    const layer005Open = (e = {}) => {
      layer005.value.layer.open(e.target);
    };

    return {
      layer001,
      layer002,
      layer003,
      layer004,
      layer005,
      layer001Open,
      layer002Open,
      layer003Open,
      layer004Open,
      layer005Open,
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
          인증 수단 선택<br />PF_M09_b001
        </BasicButton>
      </ButtonListItem>

      <ButtonListItem>
        <BasicButton @click="layer002Open">
          한도조회 동의<br />PF_M09_l001
        </BasicButton>
      </ButtonListItem>

      <ButtonListItem>
        <BasicButton @click="layer003Open">
          사업자 대출 안내<br />PF_M09_b002
        </BasicButton>
      </ButtonListItem>

      <ButtonListItem>
        <BasicButton @click="layer004Open">
          주택정보 입력<br />PF_M09_l002
        </BasicButton>
      </ButtonListItem>

      <ButtonListItem>
        <BasicButton @click="layer005Open">
          상담신청 완료<br />PF_M09_l003
        </BasicButton>
      </ButtonListItem>
    </ButtonList>

    <LayerPersonalLoanIdentificationMethodSelect ref="layer001" />
    <LayerPersonalLoanBusinessHouseAgree ref="layer002" />
    <LayerPersonalLoanBusinessHouseNotice ref="layer003" />
    <LayerPersonalLoanBusinessHouseForm ref="layer004" />
    <LayerPersonalLoanBusinessHouseComplete ref="layer005" />
  </PageContents>
</template>
