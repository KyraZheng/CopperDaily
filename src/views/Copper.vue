<template>
  <Layout>
    <div class="tags">
      <ul class="current">
        <li>衣</li>
        <li>食</li>
        <li>住</li>
        <li>行</li>
      </ul>
      <div class="new">
        <button>新增标签</button>
      </div>
    </div>
    <div>
      <label class="notes">
        <span class="name">备注</span>
        <input type="text" placeholder="在这里输入备注">
      </label>
    </div>
    <div>
      <ul class="types">
        <li class="selected">支出</li>
        <li>收入</li>
      </ul>
    </div>
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
  </Layout>
</template>

<script lang="ts">
  export default {
    name: 'Copper'
  }
</script>

<style lang="scss" scoped>
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
      height: 64px;
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

  .notes {
    background: #f5f5f5;
    display: block;
    padding: 0 16px;
    display: flex;
    align-items: center;

    .name {
      padding-right: 16px;

    }

    input {
      height: 60px;
      flex-grow: 1;
      background: transparent;
      border: none;
    }
  }

  .tags {
    padding: 16px;
    font-size: 14px;

    > .current {
      display: flex;

      > li {
        line-height: 24px;
        height: 24px;
        border-radius: 12px;
        background: #d9d9d9;
        margin-right: 10px;
        padding: 0 16px;
      }
    }

    > .new {
      padding-top: 16px;

      button {
        background: transparent;
        border: none;
        border-bottom: 1px solid;
        color: #999;
        padding: 0 3px;
      }
    }
  }
</style>