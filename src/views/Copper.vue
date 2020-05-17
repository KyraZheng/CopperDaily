<template>
  <Layout content-class="xxx">
    <NumberPad/>
    <Types/>
    <Notes/>
    <Tags :data-source="tags"/>
  </Layout>
</template>

<script>
  import Notes from '@/components/Copper/Notes.vue'
  import NumberPad from '@/components/Copper/NumberPad.vue'
  import Tags from '@/components/Copper/Tags.vue'
  import Types from '@/components/Copper/Types.vue'

  export default {
    name: 'Copper',
    components: {Types, Tags, NumberPad, Notes},
    data() {
      return {
    tags:['衣','食','住','行']
  }}}
</script>

<style lang="scss">
  .xxx {
    display: flex;
    flex-direction: column-reverse;
  }
</style>
