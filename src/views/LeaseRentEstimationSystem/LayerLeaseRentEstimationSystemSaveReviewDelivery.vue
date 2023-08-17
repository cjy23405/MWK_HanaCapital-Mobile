<script>
// LR_M04_l001
import { ref, reactive } from 'vue';

import UiLayer from '@/components/ui/layer/UiLayer.vue';
import PopupButton from '@/components/ui/layer/PopupButton.vue';
import FullPopup from '@/components/ui/layer/FullPopup.vue';
import FullPopupHead from '@/components/ui/layer/FullPopupHead.vue';
import ButtonList from '@/components/ui/button/ButtonList.vue';
import ButtonListItem from '@/components/ui/button/ButtonListItem.vue';
import BasicButton from '@/components/ui/button/BasicButton.vue';
import PageTextGroup from '@/components/ui/text/PageTextGroup.vue';
import PageMainText from '@/components/ui/text/PageMainText.vue';
import PageSubText from '@/components/ui/text/PageSubText.vue';
import InputBlock from '@/components/ui/form/InputBlock.vue';
import InputBlockCell from '@/components/ui/form/InputBlockCell.vue';
import BasicInput from '@/components/ui/form/BasicInput.vue';
import FormList from '@/components/ui/form/FormList.vue';
import FormListItem from '@/components/ui/form/FormListItem.vue';
import FormInvalid from '@/components/ui/form/FormInvalid.vue';
import FormInvalidMessage from '@/components/ui/form/FormInvalidMessage.vue';
import FormHelpText from '@/components/ui/form/FormHelpText.vue';
import BasicSelect from '@/components/ui/form/BasicSelect.vue';
import BasicDatepicker from '@/components/ui/form/BasicDatepicker.vue';
import BasicTextarea from '@/components/ui/form/BasicTextarea.vue';

export default {
  components: {
    UiLayer,
    PopupButton,
    FullPopup,
    FullPopupHead,
    ButtonList,
    ButtonListItem,
    BasicButton,
    PageTextGroup,
    PageMainText,
    PageSubText,
    InputBlock,
    InputBlockCell,
    BasicInput,
    FormList,
    FormListItem,
    FormInvalid,
    FormInvalidMessage,
    FormHelpText,
    BasicSelect,
    BasicDatepicker,
    BasicTextarea,
  },
  setup() {
    const state = reactive({
      nameError001: false,
      nameError002: false,
      NumberError001: false,
      NumberError002: false,
      dateError: false,
      timeError: false,
      addressError: false,
      noteError: false,
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
          <template v-slot:right>
            <PopupButton @click="layerSlotProps.close()" />
          </template>
        </FullPopupHead>
      </template>

      <PageTextGroup>
        <PageMainText>
          차량 인도 정보를<br />
          <strong>입력해 주세요</strong>
        </PageMainText>
        <PageSubText>하나캐피탈 탁송을 신청합니다.</PageSubText>
      </PageTextGroup>

      <FormList>
        <FormListItem
          titleText="인도지 담당자"
          :require="true"
          target="#layerLeaseRentEstimationSystemSaveReviewDeliveryName001"
        >
          <FormInvalid :error="state.nameError001">
            <InputBlock :error="state.nameError001">
              <InputBlockCell :flexible="true">
                <BasicInput
                  title="인도지 담당자"
                  id="layerLeaseRentEstimationSystemSaveReviewDeliveryName001"
                />
              </InputBlockCell>
            </InputBlock>
            <FormInvalidMessage>Error Message</FormInvalidMessage>
          </FormInvalid>
        </FormListItem>

        <FormListItem
          titleText="담당자 연락처"
          :require="true"
          target="#layerLeaseRentEstimationSystemSaveReviewDeliveryNumber001"
        >
          <FormInvalid :error="state.NumberError001">
            <InputBlock :error="state.NumberError001">
              <InputBlockCell :flexible="true">
                <BasicInput
                  type="number"
                  pattern="\d*"
                  title="담당자 연락처"
                  id="layerLeaseRentEstimationSystemSaveReviewDeliveryNumber001"
                />
              </InputBlockCell>
            </InputBlock>
            <FormInvalidMessage>Error Message</FormInvalidMessage>
            <FormHelpText>숫자만 입력해 주세요.</FormHelpText>
          </FormInvalid>
        </FormListItem>

        <FormListItem
          titleText="인도지 담당자 2"
          target="#layerLeaseRentEstimationSystemSaveReviewDeliveryName002"
        >
          <FormInvalid :error="state.nameError002">
            <InputBlock :error="state.nameError002">
              <InputBlockCell :flexible="true">
                <BasicInput
                  title="인도지 담당자 2"
                  id="layerLeaseRentEstimationSystemSaveReviewDeliveryName002"
                />
              </InputBlockCell>
            </InputBlock>
            <FormInvalidMessage>Error Message</FormInvalidMessage>
          </FormInvalid>
        </FormListItem>

        <FormListItem
          titleText="담당자 연락처 2"
          target="#layerLeaseRentEstimationSystemSaveReviewDeliveryNumber002"
        >
          <FormInvalid :error="state.NumberError002">
            <InputBlock :error="state.NumberError002">
              <InputBlockCell :flexible="true">
                <BasicInput
                  type="number"
                  pattern="\d*"
                  title="담당자 연락처 2"
                  id="layerLeaseRentEstimationSystemSaveReviewDeliveryNumber002"
                />
              </InputBlockCell>
            </InputBlock>
            <FormInvalidMessage>Error Message</FormInvalidMessage>
            <FormHelpText>숫자만 입력해 주세요.</FormHelpText>
          </FormInvalid>
        </FormListItem>

        <FormListItem
          titleText="인도 요청일"
          :require="true"
          target="#layerLeaseRentEstimationSystemSaveReviewDeliveryDateButton"
        >
          <FormInvalid :error="state.dateError">
            <InputBlock :error="state.dateError">
              <InputBlockCell :flexible="true">
                <BasicDatepicker
                  title="인도 요청일"
                  id="layerLeaseRentEstimationSystemSaveReviewDeliveryDate"
                  buttonId="layerLeaseRentEstimationSystemSaveReviewDeliveryDateButton"
                />
              </InputBlockCell>
            </InputBlock>
            <FormInvalidMessage>Error Message</FormInvalidMessage>
          </FormInvalid>
        </FormListItem>

        <FormListItem
          titleText="인도 요청 시간"
          :require="true"
          target="#layerLeaseRentEstimationSystemSaveReviewDeliveryHourButton"
        >
          <FormInvalid :error="state.timeError">
            <InputBlock :error="state.timeError">
              <InputBlockCell :flexible="true">
                <BasicSelect
                  :option="[
                    {
                      value: '9',
                      text: '9',
                    },
                    {
                      value: '10',
                      text: '10',
                    },
                  ]"
                  buttonTitle="시 선택하기"
                  layerTitle="시를 선택해 주세요"
                  id="layerLeaseRentEstimationSystemSaveReviewDeliveryHour"
                  buttonId="layerLeaseRentEstimationSystemSaveReviewDeliveryHourButton"
                />
              </InputBlockCell>
              <InputBlockCell margin="regular">
                <div class="text-body-3">시</div>
              </InputBlockCell>
              <InputBlockCell margin="regular">
                <div class="text-body-3">~</div>
              </InputBlockCell>
              <InputBlockCell :flexible="true" margin="regular">
                <BasicSelect
                  :option="[
                    {
                      value: '00',
                      text: '00',
                    },
                    {
                      value: '30',
                      text: '30',
                    },
                  ]"
                  buttonTitle="분 선택하기"
                  layerTitle="분을 선택해 주세요"
                  id="layerLeaseRentEstimationSystemSaveReviewDeliveryMinute"
                  buttonId="layerLeaseRentEstimationSystemSaveReviewDeliveryMinuteButton"
                />
              </InputBlockCell>
              <InputBlockCell margin="regular">
                <div class="text-body-3">분</div>
              </InputBlockCell>
            </InputBlock>
            <FormInvalidMessage>Error Message</FormInvalidMessage>
          </FormInvalid>
        </FormListItem>

        <FormListItem
          titleText="인도지 주소"
          :forceFocus="true"
          :require="true"
          target="#layerLeaseRentEstimationSystemSaveReviewDeliveryAddressSearch"
        >
          <FormInvalid :error="state.addressError">
            <InputBlock :error="state.addressError">
              <InputBlockCell :flexible="true">
                <BasicInput
                  title="인도지 우편번호"
                  :disabled="true"
                  defaultValue="06123"
                />
              </InputBlockCell>
              <template v-slot:right>
                <BasicButton
                  size="mini"
                  theme="tertiary"
                  id="layerLeaseRentEstimationSystemSaveReviewDeliveryAddressSearch"
                  >검색</BasicButton
                >
              </template>
            </InputBlock>
            <!-- DD : 주소 검색 및 입력 후 노출 -->
            <InputBlock
              :error="state.addressError"
              :classNames="{
                wrap: 'row-margin-item-group row-margin-bottom-none',
              }"
            >
              <InputBlockCell :flexible="true">
                <BasicInput
                  title="인도지 도로명 주소"
                  :disabled="true"
                  defaultValue="서울 중구 을지로 35"
                />
              </InputBlockCell>
            </InputBlock>
            <InputBlock
              :error="state.addressError"
              :classNames="{
                wrap: 'row-margin-item-group row-margin-bottom-none',
              }"
            >
              <InputBlockCell :flexible="true">
                <BasicInput
                  title="인도지 상세 주소"
                  :disabled="true"
                  defaultValue="1205호"
                />
              </InputBlockCell>
            </InputBlock>
            <!-- // DD : 주소 검색 및 입력 후 노출 -->
            <FormInvalidMessage>Error Message</FormInvalidMessage>
          </FormInvalid>
        </FormListItem>

        <BasicTextarea :error="state.noteError" titleText="비고" title="비고">
          <template v-slot:bottom>
            <FormInvalidMessage>Error Message</FormInvalidMessage>
          </template>
        </BasicTextarea>
      </FormList>

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
            <BasicButton>다음</BasicButton>
          </ButtonListItem>
        </ButtonList>
      </template>
    </FullPopup>
  </UiLayer>
</template>