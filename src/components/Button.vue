<template>
  <button class="button" @click="$emit('click',$event)">
    <slot/>
  </button>
</template>

<script lang="ts">
  import Vue from 'vue';
  import {Component} from 'vue-property-decorator';

  @Component
  export default class Button extends Vue {}
</script>

<style scoped lang="scss">
  .button {
    background: cadetblue;
    border-radius: 4px;
    border: none;
    color: white;
    height: 40px;
    padding: 0 12px;

    &-wrapper {
      text-align: center;
      padding: 16px;
      margin-top: 40-16px;
    }
  }
</style>