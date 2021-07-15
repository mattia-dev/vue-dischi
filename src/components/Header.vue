<template>
  <header>
    <img src="../assets/spotify-logo.png" alt="spotify-logo">
  </header>
</template>

<script>
export default {
  name: 'Header',
  props: {
    
  }
}
</script>

<style scoped lang="scss">
@import "../style/colors";

header {
    height: 80px;
    background-color: $bg-secondary;
     
    img {
        height: 100%;
        padding: 12px 24px;
    }  
}
</style>