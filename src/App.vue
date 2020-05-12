<template>
  <div id="app">
    <div class="title">布泉记账</div>
    <router-view/>
  </div>
</template>

<style lang="scss">
  @import "~@/assets/style/helper.scss";
  @import "~@/assets/style/reset.scss";
  body{
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    line-height: 1.5;
    font-family: $font-hei;
  }
  .title {
padding-left: 12px;
    height: 9vh;
    background: CadetBlue;
    font-size: 30px;
    color: white;
    line-height:9vh;

  }
</style>
