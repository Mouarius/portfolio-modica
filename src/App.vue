<script>

import NavBar from "./components/NavBar.vue"
import ElementPhoto from "./components/ElementPhoto.vue"

export default {
  name: 'App',
  components: {
    NavBar, ElementPhoto
  },
  data(){
    return{
      image1:{
        id:1,
        source:"/images/photos/village-1.jpg",
        alt:"Village de cases en Afrique."
      } 
    }
  }
}
</script>

<template>
  <div id="app">
    <div id="main-window">
      <NavBar />
      <section id="defilement-photos">
        <ElementPhoto :image="image1"></ElementPhoto>
    </section>
    </div>
  </div>
</template>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
body{
  margin: 0px;
}
</style>
