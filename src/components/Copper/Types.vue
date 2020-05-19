<template>
  <div>
    <ul class="types">
      <li :class="value === '-' && 'selected' " @click="selectType('-')">支出</li>
      <li :class="value === '+' && 'selected' " @click="selectType('+')">收入</li>
    </ul>
  </div>
</template>

<script lang="ts">
  import Vue from 'vue';
  import {Component, Prop, Watch} from 'vue-property-decorator';

  @Component

  export default class Types extends Vue {
    @Prop() readonly value!: string;

    selectType(type: string) {
      if (type !== '+' && type !== '-') {
        throw new Error('type is unknown');
      }
      this.$emit('update:value',type)
    }

    @Watch('type')
    onTypeChanged(value: string) {
      this.$emit('update:value', value);
    }
  }

</script>

<style scoped lang="scss">
  .types {
    background: #d9d9d9;
    display: flex;
    text-align: center;
    font-size: 24px;

    > li {
      width: 50%;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 62px;
      position: relative;

      &.selected::after {
        content: '';
        bottom: 0;
        left: 0;
        width: 100%;
        position: absolute;
        height: 4px;
        background: CadetBlue;
      }
    }
  }
</style>