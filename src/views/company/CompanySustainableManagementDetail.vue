<script>
// Company_M08_p008
import { onMounted, onUnmounted } from 'vue';

import { useUiHeaderStore } from '@/stores/ui/header';

import PageContents from '@/components/ui/layout/PageContents.vue';
import BasicButton from '@/components/ui/button/BasicButton.vue';
import ButtonList from '@/components/ui/button/ButtonList.vue';
import ButtonListItem from '@/components/ui/button/ButtonListItem.vue';
import DownloadButton from '@/components/ui/button/DownloadButton.vue';

export default {
  components: {
    PageContents,
    BasicButton,
    ButtonList,
    ButtonListItem,
    DownloadButton,
  },
  setup() {
    const store = {
      ui: {
        header: useUiHeaderStore(),
      },
    };

    onMounted(() => {
      store.ui.header.setTitle(() => '지속가능경영');
      store.ui.header.setLeftButtons(() => ['back']);
      store.ui.header.setRightButtons(() => []);
    });

    onUnmounted(() => {
      store.ui.header.setTitle();
      store.ui.header.setLeftButtons();
      store.ui.header.setRightButtons();
    });
  },
};
</script>

<template>
  <PageContents>
    <div :class="$style['board-detail']">
      <div :class="$style['board-detail__head']">
        <h2 :class="$style['board-detail__title']">ESG채권 투자자 안내문</h2>
        <p :class="$style['board-detail__sub']">2022.08.09</p>
      </div>

      <section :class="$style['board-detail__contents']">
        //게시물 내용 노출
      </section>

      <div :class="$style['board-detail__foot']">
        <ul class="reset-list">
          <li class="row-margin-item-group">
            <div class="flex-box">
              <div class="flex-box__cell flex-1">
                <div class="text-body-4 font-weight-medium">
                  하나캐피탈 ESG채권 투자자 안내문.pdf
                </div>
              </div>
              <div class="flex-box__cell">
                <DownloadButton tagName="a" href="/foo/bar.pdf" download />
              </div>
            </div>
          </li>
          <li class="row-margin-item-group">
            <div class="flex-box">
              <div class="flex-box__cell flex-1">
                <div class="text-body-4 font-weight-medium">
                  하나캐피탈 ESG채권 투자자 안내문.pdf
                </div>
              </div>
              <div class="flex-box__cell">
                <DownloadButton tagName="a" href="/foo/bar.pdf" download />
              </div>
            </div>
          </li>
        </ul>
      </div>
    </div>

    <ButtonList>
      <ButtonListItem>
        <BasicButton
          :line="true"
          theme="quaternary"
          tagName="RouterLink"
          to="/company/sustainable-management-list"
        >
          목록
        </BasicButton>
      </ButtonListItem>
    </ButtonList>
  </PageContents>
</template>

<style lang="scss" module>
@import '@/assets/scss/views/company/CompanySustainableManagementDetail.scss';
</style>
