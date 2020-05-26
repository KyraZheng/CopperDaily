<template>
  <Layout>
    <div class="tags">
      <router-link class="tag" v-for="tag in tags" :key="tag.id" :to="`/labels/edit/${tag.id}`">
        <span>{{tag.name}}</span>
        <Icon name="right"/>
      </router-link>
    </div>
    <div class="createTag-wrapper">
      <Button class="createTag" @click="createTag">
        新建标签
      </Button>
    </div>
  </Layout>
</template>

<script lang="ts">

  import Vue from 'vue';
  import {Component} from 'vue-property-decorator';
  import Button from '@/components/Button.vue';
  import store from '@/store/index2';

  @Component({
    components: {Button}
  })
  export default class Labels extends Vue {
    tags = store.tagList;

    createTag() {
      const name = window.prompt('请输入标签名');
      if (name) {
        store.createTag(name);
      }
    }

  }
</script>

<style lang="scss">
  .tags {
    padding-left: 16px;
    font-size: 16px;
    background: white;

    .tag {
      min-height: 44px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      border-bottom: 1px solid #e6e6e6;

      > svg {
        margin-right: 16px;
        color: #555;
      }
    }
  }

  .createTag {
    background: cadetblue;
    border-radius: 4px;
    border: none;
    color: white;
    height: 40px;
    padding: 0 12px;

    &-wrapper {
      text-align: center;
      padding: 16px;
      margin-top: 40-16px;
    }
  }
</style>