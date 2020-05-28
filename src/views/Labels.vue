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
  import {mixins} from 'vue-class-component';
  import TagHelper from '@/mixins/TagHelper';

  @Component({
    components: {Button},
    computed: {
      tags() {
        return this.$store.state.tagList;
      },
    }
  })
  export default class Labels extends mixins(TagHelper) {
    beforeCreate() {
      this.$store.commit('fetchTags');
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