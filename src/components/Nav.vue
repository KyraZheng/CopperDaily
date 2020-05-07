<template>
  <div class="nav">
  <router-link to="/labels">标签</router-link>|
  <router-link to="/copper">记一笔</router-link> |
  <router-link to="/statistics">统计</router-link>
  </div>
</template>

<script lang="ts">
  import x from '@/assets/icons/labels.svg'
  export default {
    name: 'Nav'
  }
</script>

<style scoped lang="scss">
.nav {
  border: 1px solid red;

}
</style>