<template>
  <main>
    <div class="container">
        <div class="row">
            <Album class="col-6" v-for="(album, index) in albums" :key="index"
                :cover="album.poster"
                :title="album.title"
                :artist="album.author"
                :year="album.year"
            />
        </div>
    </div>
  </main>
</template>

<script>
import Album from './Album.vue'

export default {
  name: 'Main',
  components: {
    Album,
  },
  props: {
    albums: Array
  }
}
</script>

<style scoped lang="scss">

</style>