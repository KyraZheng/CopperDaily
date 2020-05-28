<template>
  <Layout content-class="contentClass">
    <NumberPad @update:value="onUpdateAmount" @submit="saveRecord"/>
    <Types :value.sync="record.type"/>
    <div class="notes">
      <FormItem field-name="备注" placeholder="在这里输入备注" @update:value="onUpdateNotes"/>
    </div>
    <Tags/>
  </Layout>
</template>

<script lang="ts">
  import Vue from 'vue';
  import FormItem from '@/components/Copper/FormItem.vue';
  import NumberPad from '@/components/Copper/NumberPad.vue';
  import Tags from '@/components/Copper/Tags.vue';
  import Types from '@/components/Copper/Types.vue';
  import {Component} from 'vue-property-decorator';
  import store from '@/store/index2';

  @Component({
    components: {FormItem, Types, Tags, NumberPad,}
  })

  export default class Copper extends Vue {
    recordList = store.recordList;
    record: RecordItem = {
      tags: [], notes: '', type: '-', amount: 0
    };

    onUpdateNotes(value: string) {
      this.record.notes = value;
    }

    onUpdateAmount(value: string) {
      this.record.amount = parseFloat(value);
    }

    saveRecord() {
      store.createRecord(this.record);
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
