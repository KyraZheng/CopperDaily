<template>
  <div class="numberPad">
    <div class="output">100</div>
    <div class="buttons">
      <button>1</button>
      <button>2</button>
      <button>3</button>
      <button>DEL</button>
      <button>4</button>
      <button>5</button>
      <button>6</button>
      <button class="OK">OK</button>
      <button>7</button>
      <button>8</button>
      <button>9</button>
      <button>C</button>

      <button class="zero">0</button>
      <button>.</button>
    </div>
  </div>
</template>

<script lang="ts">
  export default {
    name: 'NumberPad'
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