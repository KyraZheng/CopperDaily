<template>
  <div class="numberPad">
    <div class="output">{{output}}</div>
    <div class="buttons">
      <button @click="inputContent">1</button>
      <button @click="inputContent">2</button>
      <button @click="inputContent">3</button>
      <button @click="remove">DEL</button>
      <button @click="inputContent">4</button>
      <button @click="inputContent">5</button>
      <button @click="inputContent">6</button>
      <button @click="ok" class="OK">OK</button>
      <button @click="inputContent">7</button>
      <button @click="inputContent">8</button>
      <button @click="inputContent">9</button>
      <button @click="clear">C</button>

      <button @click="inputContent" class="zero">0</button>
      <button @click="inputContent">.</button>
    </div>
  </div>
</template>

<script lang="ts">
  import Vue from 'vue';
  import {Component} from 'vue-property-decorator';

  @Component

  export default class NumberPad extends Vue {
    output = '0';

    inputContent(event: MouseEvent) {
      const button = (event.target as HTMLButtonElement);
      const input = button.textContent!;
      if (this.output.length === 16) {return;}
      if (this.output === '0') {
        if ('0123456789'.indexOf(input) >= 0) {
          this.output = input;
        } else {
          this.output += input;
        }
        return;
      }
      if (this.output.indexOf('.') >= 0 && input === '.') {return;}
      this.output += input;
    }

    remove() {
      if (this.output.length === 1) {
        this.output = '0';
      } else {
        this.output = this.output.slice(0, -1);
      }
    }

    clear() {
      this.output = '0';
    }

    ok() {
      this.$emit('update:value', this.output);
    }
  }

</script>

<style scoped lang="scss">
  @import "~@/assets/style/helper.scss";

  .numberPad {
    .output {
      font-size: 36px;
      font-family: Consolas, monospace;
      padding: 9px 16px;
      text-align: right;
      height: 72px;
      box-shadow: inset 0 -5px 5px -5px fade_out(rgb(0, 0, 0, 0.25), 1),
      inset 0 5px 5px -5px fade_out(rgb(0, 0, 0, 0.25), 1);
    }

    .buttons {
      @extend %clearFix;

      > button {
        border: none;
        height: 64px;
        width: 25%;
        float: left;

        &.OK {
          height: 64*3px;
          float: right;
        }

        $bg: #f5f5f5;

        &:nth-child(1) {
          background: $bg;
        }

        &:nth-child(2), &:nth-child(5), {
          background: darken($bg, 3%);
        }

        &:nth-child(3), &:nth-child(6), &:nth-child(9), {
          background: darken($bg, 6%);
        }

        &:nth-child(7), &:nth-child(10), &:nth-child(12), {
          background: darken($bg, 9%);
        }

        &:nth-child(11), &:nth-child(13), {
          background: darken($bg, 12%);
        }

        &:nth-child(14), {
          background: darken($bg, 15%);
        }

        &:nth-child(4) {
          background: lighten(cadetblue, 35%);
        }

        &:nth-child(8) {
          background: lighten(cadetblue, 30%);
        }
      }
    }
  }
</style>