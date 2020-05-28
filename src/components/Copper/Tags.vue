<template>
  <div class="tags">
    <div class="new">
      <button @click="create">新增标签</button>
    </div>
    <ul class="current">
      <li v-for="tag in tagList" :key="tag.id"
          :class="{selected: selectedTags.indexOf(tag)>=0}"
          @click="toggle(tag)">{{tag.name}}
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
  import Vue from 'vue';
  import {Component, Prop} from 'vue-property-decorator';
  import store from '@/store/index2';

  @Component
  export default class Tags extends Vue {
    tagList = store.fetchTags();
    selectedTags: string[] = [];

    toggle(tag: string) {
      const index = this.selectedTags.indexOf(tag);
      if (index >= 0) {
        this.selectedTags.splice(index, 1);
      } else {
        this.selectedTags.push(tag);
      }
      this.$emit('update:value', this.selectedTags);
    }

    create() {
      const name = window.prompt('请输入标签名');
      if (!name) { return window.alert('标签名不能为空'); }
      store.createTag(name);
    }
  }
</script>

<style scoped lang="scss">
  .tags {
    background: white;
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

        &.selected {
          background: lighten(cadetblue, 20%);
        }
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