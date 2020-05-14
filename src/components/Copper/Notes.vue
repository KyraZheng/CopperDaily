<template>
  <div>
    <label class="notes">
      <span class="name">备注</span>
      <input type="text" placeholder="在这里输入备注">
    </label>
  </div>
</template>

<script lang="ts">
  export default {
    name: 'Notes'
  }
</script>

<style scoped lang="scss">
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
      height: 58px;
      flex-grow: 1;
      background: transparent;
      border: none;
    }
  }
</style>