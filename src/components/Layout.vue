<template>
  <div class="layout-wrapper"     >
    <div class="content" :class="contentClass">
      <slot/>

    </div>
    <Nav/>

  </div>

</template>

<script lang="ts">
  export default {
    props:['contentClass'],
    name: 'Layout'

  }
</script>

<style scoped lang="scss">
  .layout-wrapper {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
  }
  .content {
    overflow: auto;
    flex-grow: 1;
  }
</style>