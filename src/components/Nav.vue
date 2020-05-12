<template>
  <nav>
  <router-link to="/labels" class="item" active-class="selected">
    <Icon name="labels"/>
    标签
  </router-link>
  <router-link to="/copper" class="item" active-class="selected">
    <Icon name="copper"/>
    记一笔
  </router-link>
  <router-link to="/statistics" class="item" active-class="selected">
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

<style lang="scss" scoped >
nav {
  display: flex;
  box-shadow: 0 0 3px rgba(0,0,0,0.25);
  flex-direction: row;
  padding:3px;
  font-size: 12px;
color: #444444;

  > .item {
  padding: 2px 0;
  width: 33.333333%;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
 .icon {
  width: 32px;
  height: 32px;
}
}
 > .item.selected {
  color: CadetBlue;
}
}
</style>