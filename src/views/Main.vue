<template>
  <div>
    <a-card>
      <div class="flex response justify-between">
        <range-picker style="width:200px;" v-model="dates"></range-picker>

        <multiple-choice-box placeholder="请选择"
                             v-model="value"
                             :bordered="true"
                             :required="true"
                             :tree-data="treeData"></multiple-choice-box>
      </div>
    </a-card>

    <!--tabs-->
    <a-card>
      <!--      <a-locale-provider :locale="locale">-->
      <!--        <router-view :key="$route.fullPath"></router-view>-->
      <!--      </a-locale-provider>-->

      <tabs-modal-preview></tabs-modal-preview>
    </a-card>
  </div>
</template>

<script lang="ts">

import { Component, Vue } from 'vue-property-decorator';
import MultipleChoiceBox from '@/components/select/MultipleChoiceBox.vue';
import RangePicker from '@/components/select/RangePicker.vue';
import $ from 'jquery';
import TabsModalPreview from '@/views/tabs/tabsModal_preview.vue';

@Component({
  name: 'Main',
  components: { TabsModalPreview, RangePicker, MultipleChoiceBox },
})
export default class Main extends Vue {
  value = ['黎明-01', '黎明-02'];

  treeData: any[] = [
    {
      title: '四大天王',
      key: 'root',
      children: [
        {
          title: '张学友',
          key: '张学友',
          children: [
            { key: '张学友-01', title: '张学友1' },
            {
              key: '张学友-02',
              title: '张学友2',
              children: [
                {
                  key: '张学友-02-01',
                  title: '张学友2-01',
                },
              ],
            }],
        },
        {
          title: '黎明',
          key: '黎明',
          children: [
            { title: '黎明1', key: '黎明-01' },
            { title: '黎明2', key: '黎明-02' },
          ],
          // scopedSlots: { title: 'title' },
        },
        {
          title: '刘德华',
          key: '刘德华',
          children: [{ key: '刘德华-01', title: '刘德华1' }],
        },
        {
          title: '郭富城',
          key: '郭富城',
          children: [
            { key: '郭富城-01', title: '郭富城1' },
            { key: '郭富城-02', title: '郭富城2' }],
        },
      ],
    },
  ];

  dates = ['2021-01-03T08:51:22.384Z', '2021-02-25T08:51:22.384Z'];
}
</script>

<style scoped>

</style>
