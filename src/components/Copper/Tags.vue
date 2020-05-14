<template>
  <div class="tags">
    <div class="new">
      <button>新增标签</button>
    </div>
    <ul class="current">
      <li>衣</li>
      <li>食</li>
      <li>住</li>
      <li>行</li>
    </ul>

  </div>
</template>

<script lang="ts">
  export default {
    name: 'Tags'
  }
</script>

<style scoped lang="scss">
  .tags {
    display: flex;
    flex-direction: column-reverse;
    flex-grow: 1;
    padding: 16px;
    font-size: 14px;

    > .current {
      flex-wrap: wrap;
      display: flex;

      > li {
        line-height: 24px;
        height: 24px;
        border-radius: 12px;
        background: #d9d9d9;
        margin-right: 10px;
        padding: 0 16px;
        margin-top: 4px;
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