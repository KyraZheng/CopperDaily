<template>
  <Layout content-class="contentClass">
    {{records}}
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

  window.localStorage.setItem('version', '0.0.1');

  type Record = {
    tags: string[];
    notes: string;
    type: string;
    amount: number;
    createdAt?: Date
  }

  @Component({
    components: {Types, Tags, NumberPad, Notes}
  })

  export default class Copper extends Vue {

    tags = ['衣', '食', '住', '行'];
    records: Record = JSON.parse(window.localStorage.getItem('records') || '[]');
    record: Record = {
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
      const record2: Record = JSON.parse(JSON.stringify(this.record));
      record2.createdAt = new Date();
      this.records.push(record2);
    }

    @Watch('records')
    onRecordListChange() {
      window.localStorage.setItem('records', JSON.stringify(this.records));
    }
  }
</script>

<style lang="scss">
  .contentClass {
    display: flex;
    flex-direction: column-reverse;
  }
</style>
