<script>
import { ref } from 'vue';

import PageContents from '@/components/ui/layout/PageContents.vue';
import BasicButton from '@/components/ui/button/BasicButton.vue';
import ButtonList from '@/components/ui/button/ButtonList.vue';
import ButtonListItem from '@/components/ui/button/ButtonListItem.vue';

import LayerEquipmentLeaseEstimateSchedule from '@/views/equipmentLease/LayerEquipmentLeaseEstimateSchedule.vue';
import LayerEquipmentLeaseEstimateSend from '@/views/equipmentLease/LayerEquipmentLeaseEstimateSend.vue';
import LayerEquipmentLeaseEstimateURL from '@/views/equipmentLease/LayerEquipmentLeaseEstimateURL.vue';
import LayerEquipmentLeaseEstimateURLSchedule from '@/views/equipmentLease/LayerEquipmentLeaseEstimateURLSchedule.vue';
import LayerEquipmentLeaseStatePriorAgree from '@/views/equipmentLease/LayerEquipmentLeaseStatePriorAgree.vue';
import LayerEquipmentLeaseStateCounselingAgree from '@/views/equipmentLease/LayerEquipmentLeaseStateCounselingAgree.vue';
import LayerEquipmentLeaseStateElectronicContract from '@/views/equipmentLease/LayerEquipmentLeaseStateElectronicContract.vue';
import LayerEquipmentLeaseStateDetail from '@/views/equipmentLease/LayerEquipmentLeaseStateDetail.vue';
import LayerEquipmentLeaseStateAgree from '@/views/equipmentLease/LayerEquipmentLeaseStateAgree.vue';
import LayerEquipmentLeaseStateComplete from '@/views/equipmentLease/LayerEquipmentLeaseStateComplete.vue';
import EL_M02_l007 from '@/views/equipmentLease/EL_M02_l007.vue';
import EL_M02_l008 from '@/views/equipmentLease/EL_M02_l008.vue';
import EL_M02_l009 from '@/views/equipmentLease/EL_M02_l009.vue';
import EL_M02_l010 from '@/views/equipmentLease/EL_M02_l010.vue';

export default {
  components: {
    PageContents,
    BasicButton,
    ButtonList,
    ButtonListItem,
    LayerEquipmentLeaseEstimateSchedule,
    LayerEquipmentLeaseEstimateSend,
    LayerEquipmentLeaseEstimateURL,
    LayerEquipmentLeaseEstimateURLSchedule,
    LayerEquipmentLeaseStatePriorAgree,
    LayerEquipmentLeaseStateCounselingAgree,
    LayerEquipmentLeaseStateElectronicContract,
    LayerEquipmentLeaseStateDetail,
    LayerEquipmentLeaseStateAgree,
    LayerEquipmentLeaseStateComplete,
    EL_M02_l007,
    EL_M02_l008,
    EL_M02_l009,
    EL_M02_l010,
  },
  setup() {
    const layer001 = ref(null);
    const layer002 = ref(null);
    const layer003 = ref(null);
    const layer004 = ref(null);
    const layer005 = ref(null);
    const layer006 = ref(null);
    const layer007 = ref(null);
    const layer008 = ref(null);
    const layer009 = ref(null);
    const layer010 = ref(null);
    const layer011 = ref(null);
    const layer012 = ref(null);
    const layer013 = ref(null);
    const layer014 = ref(null);

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
    const layer006Open = (e = {}) => {
      layer006.value.layer.open(e.target);
    };
    const layer007Open = (e = {}) => {
      layer007.value.layer.open(e.target);
    };
    const layer008Open = (e = {}) => {
      layer008.value.layer.open(e.target);
    };
    const layer009Open = (e = {}) => {
      layer009.value.layer.open(e.target);
    };
    const layer010Open = (e = {}) => {
      layer010.value.layer.open(e.target);
    };
    const layer011Open = (e = {}) => {
      layer011.value.layer.open(e.target);
    };
    const layer012Open = (e = {}) => {
      layer012.value.layer.open(e.target);
    };
    const layer013Open = (e = {}) => {
      layer013.value.layer.open(e.target);
    };
    const layer014Open = (e = {}) => {
      layer014.value.layer.open(e.target);
    };

    return {
      layer001,
      layer002,
      layer003,
      layer004,
      layer005,
      layer006,
      layer007,
      layer008,
      layer009,
      layer010,
      layer011,
      layer012,
      layer013,
      layer014,
      layer001Open,
      layer002Open,
      layer003Open,
      layer004Open,
      layer005Open,
      layer006Open,
      layer007Open,
      layer008Open,
      layer009Open,
      layer010Open,
      layer011Open,
      layer012Open,
      layer013Open,
      layer014Open,
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
          예상 상환스케쥴<br />EL_M01_l001
        </BasicButton>
      </ButtonListItem>
      <ButtonListItem>
        <BasicButton @click="layer002Open">
          견적서 전송 정보 입력<br />EL_M01_l002
        </BasicButton>
      </ButtonListItem>
      <ButtonListItem>
        <BasicButton @click="layer003Open">
          견적 확인<br />EL_M01_l004
        </BasicButton>
      </ButtonListItem>
      <ButtonListItem>
        <BasicButton @click="layer004Open">
          견적서 고객 전송 URL - 예상 상환스케쥴<br />EL_M01_l005
        </BasicButton>
      </ButtonListItem>
      <ButtonListItem>
        <BasicButton @click="layer005Open">
          사전동의 요청 정보 입력 팝업<br />EL_M02_l001
        </BasicButton>
      </ButtonListItem>
      <ButtonListItem>
        <BasicButton @click="layer006Open">
          상담동의 요청 정보 입력 팝업<br />EL_M02_l002
        </BasicButton>
      </ButtonListItem>
      <ButtonListItem>
        <BasicButton @click="layer007Open">
          전자약정 전송 정보 입력 팝업<br />EL_M02_l003
        </BasicButton>
      </ButtonListItem>
      <ButtonListItem>
        <BasicButton @click="layer008Open">
          견적보기 팝업<br />EL_M02_l004
        </BasicButton>
      </ButtonListItem>
      <ButtonListItem>
        <BasicButton @click="layer009Open">
          신용정보조회동의<br />EL_M02_l005
        </BasicButton>
      </ButtonListItem>
      <ButtonListItem>
        <BasicButton @click="layer010Open">
          사전동의 완료<br />EL_M02_l006
        </BasicButton>
      </ButtonListItem>
      <ButtonListItem>
        <BasicButton @click="layer011Open">
          물건점검 SMS 정보 입력 팝업<br />EL_M02_l007
        </BasicButton>
      </ButtonListItem>
      <ButtonListItem>
        <BasicButton @click="layer012Open">
          본인확인(URL진입)<br />EL_M02_l008
        </BasicButton>
      </ButtonListItem>
      <ButtonListItem>
        <BasicButton @click="layer013Open">
          리스물건 점검보고서<br />EL_M02_l009
        </BasicButton>
      </ButtonListItem>
      <ButtonListItem>
        <BasicButton @click="layer014Open">
          물건점검 완료<br />EL_M02_l010
        </BasicButton>
      </ButtonListItem>
    </ButtonList>

    <LayerEquipmentLeaseEstimateSchedule ref="layer001" />
    <LayerEquipmentLeaseEstimateSend ref="layer002" />
    <LayerEquipmentLeaseEstimateURL ref="layer003" />
    <LayerEquipmentLeaseEstimateURLSchedule ref="layer004" />
    <LayerEquipmentLeaseStatePriorAgree ref="layer005" />
    <LayerEquipmentLeaseStateCounselingAgree ref="layer006" />
    <LayerEquipmentLeaseStateElectronicContract ref="layer007" />
    <LayerEquipmentLeaseStateDetail ref="layer008" />
    <LayerEquipmentLeaseStateAgree ref="layer009" />
    <LayerEquipmentLeaseStateComplete ref="layer010" />
    <EL_M02_l007 ref="layer011" />
    <EL_M02_l008 ref="layer012" />
    <EL_M02_l009 ref="layer013" />
    <EL_M02_l010 ref="layer014" />
  </PageContents>
</template>
