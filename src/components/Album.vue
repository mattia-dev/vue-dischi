<template>
  <div>
      <img :src="cover" :alt="`cover of ${title}`">
      <div>{{title}}</div>
      <div>{{artist}}</div>
      <div>{{year}}</div>
  </div>
</template>

<script>
export default {
  name: 'Album',
  props: {
    cover: String,
    title: String,
    artist: String,
    year: String,
  }
}
</script>

<style scoped lang="scss">

</style>