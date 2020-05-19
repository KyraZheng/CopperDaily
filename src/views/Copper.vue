<template>
  <Layout content-class="xxx">
    <NumberPad @update:value="onUpdateAmount" @submit="saveRecord"/>
    <Types @update:value="onUpdateType"/>
    <Notes @update:value="onUpdateNotes"/>
    <Tags  @update:value="onUpdateTags"/>
  </Layout>
</template>

<script lang="ts">
  import Vue from 'vue';
  import Notes from '@/components/Copper/Notes.vue';
  import NumberPad from '@/components/Copper/NumberPad.vue';
  import Tags from '@/components/Copper/Tags.vue';
  import Types from '@/components/Copper/Types.vue';
  import {Component, Watch} from 'vue-property-decorator';

  type Record = {
    tags: string[];
    notes: string;
    type: string;
    amount: number;
  }

  @Component({
    components: {Types, Tags, NumberPad, Notes}
  })

  export default class Copper extends Vue {

    tags = ['衣', '食', '住', '行'];
    records: Record[] = [];
    record: Record = {
      tags: [], notes: '', type: '-', amount: 0
    };

    onUpdateNotes(value: string) {
      this.record.notes = value;
    }

    onUpdateTags(value: string[]) {
      this.record.tags = value;
    }

    onUpdateType(value: string) {
      this.record.type = value;
    }

    onUpdateAmount(value: string) {
      this.record.amount = parseFloat(value);
    }

    saveRecord() {
      const record2 = JSON.parse(JSON.stringify(this.record));
      this.records.push(record2);
      console.log(this.records);
    }

    @Watch('records')
    onRecordListChange() {
      window.localStorage.setItem('records', JSON.stringify(this.records));
    }

  }
</script>

<style lang="scss">
  .xxx {
    display: flex;
    flex-direction: column-reverse;
  }
</style>
