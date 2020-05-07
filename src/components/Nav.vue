<template>
  <nav>
  <router-link to="/labels" class="item">
    <Icon name="labels"/>
    标签
  </router-link>
  <router-link to="/copper" class="item">
    <Icon name="copper"/>
    记一笔
  </router-link>
  <router-link to="/statistics" class="item">
    <Icon name="statistics"/>
    统计
  </router-link>
  </nav>
</template>

<script lang="ts">
  export default {
    name: 'Nav'
  };
</script>

<style scoped lang="scss">
nav {
  display: flex;
  box-shadow: 0 0 3px rgba(0,0,0,1);
  flex-direction: row;
  padding: 4px;

> .item {
  font-size: 14px;
  padding: 2px 0;
  width: 33.333333%;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
.icon{
  width: 32px;
  height: 32px;
}
}

}
</style>