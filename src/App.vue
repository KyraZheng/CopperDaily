<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<style lang="scss">
  @import "~@/assets/style/helper.scss";
  @import "~@/assets/style/reset.scss";

  body {
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    line-height: 1.5;
    font-family: $font-hei;
    font-size: 16px;
    background: #f5f5f5;
  }

  #app {
    max-width: 450px;
    margin: 0 auto;
  }
</style>
