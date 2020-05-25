<template>
  <Layout content-class="contentClass">
    <NumberPad @update:value="onUpdateAmount" @submit="saveRecord"/>
    <Types :value.sync="record.type"/>
    <div class="notes">
      <FormItem field-name="备注" placeholder="在这里输入备注" @update:value="onUpdateNotes"/>
    </div>
    <Tags :data-source.sync="tags" @update:value="onUpdateTags"/>
  </Layout>
</template>

<script lang="ts">
  import Vue from 'vue';
  import FormItem from '@/components/Copper/FormItem.vue';
  import NumberPad from '@/components/Copper/NumberPad.vue';
  import Tags from '@/components/Copper/Tags.vue';
  import Types from '@/components/Copper/Types.vue';
  import {Component, Watch} from 'vue-property-decorator';
  import recordListModel from '@/models/recordListModel';
  import tagListModel from '@/models/tagListModel';

  const recordList = recordListModel.fetch();

  @Component({
    components: {FormItem, Types, Tags, NumberPad,}
  })

  export default class Copper extends Vue {

    tags = window.tagList;
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
      recordListModel.create(this.record);
    }

    @Watch('recordList')
    onRecordListChange() {
      recordListModel.save();
    }
  }
</script>

<style lang="scss">
  .contentClass {
    display: flex;
    flex-direction: column-reverse;
  }

  .notes {
    padding: 12px 0;
  }
</style>
