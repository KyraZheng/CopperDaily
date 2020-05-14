<template>
  <Layout content-class="xxx">
    <NumberPad/>
    <types/>
    <notes/>
    <tags/>
  </Layout>
</template>

<script lang="ts">
  import Notes from '@/components/Copper/Notes.vue'
  import NumberPad from '@/components/Copper/NumberPad.vue'
  import Tags from '@/components/Copper/Tags.vue'
  import Types from '@/components/Copper/Types.vue'

  export default {
    name: 'Copper',
    components: {Types, Tags, NumberPad, Notes}
  }
</script>

<style lang="scss">
  .xxx {
    display: flex;
    flex-direction: column-reverse;
  }
</style>
