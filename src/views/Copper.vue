<template>
  <Layout content-class="contentClass">
    <NumberPad @update:value="onUpdateAmount" @submit="saveRecord"/>
    <Types :value.sync="record.type"/>
    <Notes @update:value="onUpdateNotes"/>
    <Tags @update:value="onUpdateTags"/>
  </Layout>
</template>

<script lang="ts">
  import Vue from 'vue';
  import Notes from '@/components/Copper/Notes.vue';
  import NumberPad from '@/components/Copper/NumberPad.vue';
  import Tags from '@/components/Copper/Tags.vue';
  import Types from '@/components/Copper/Types.vue';
  import {Component, Watch} from 'vue-property-decorator';
  import recordListModel from '@/components/models/recordListModel';
  import tagListModel from '@/components/models/tagListModel';

  const recordList = recordListModel.fetch();
  const tagList = tagListModel.fetch();

  @Component({
    components: {Types, Tags, NumberPad, Notes}
  })

  export default class Copper extends Vue {

    tags = tagList;
    recordList: RecordItem[] = recordList;
    record: RecordItem = {
      tags: [], notes: '', type: '-', amount: 0
    };

    onUpdateNotes(value: string) {
      this.record.notes = value;
    }

    onUpdateTags(value: string[]) {
      this.record.tags = value;
    }

    onUpdateAmount(value: string) {
      this.record.amount = parseFloat(value);
    }

    saveRecord() {
      const record2: RecordItem = recordListModel.clone(this.record);
      record2.createdAt = new Date();
      this.recordList.push(record2);
    }

    @Watch('records')
    onRecordListChange() {
      recordListModel.save(this.recordList);
    }
  }
</script>

<style lang="scss">
  .contentClass {
    display: flex;
    flex-direction: column-reverse;
  }
</style>
