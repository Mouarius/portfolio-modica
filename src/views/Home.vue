<script>

import Carousel from "../components/Carousel.vue"

export default {
  name: 'Home',
  components: {
    Carousel
  },
  data(){
    return{
      carousels:[
        {
          id:0,
          setOfSlides:[
            {
              id:1,
              image:{
                source:"/images/photos/village-1.jpg",
                alt:"Village de cases en Afrique."
              }
            },
            {
              id:2,
              image:{
                source:"/images/photos/mamas-1.jpg",
                alt:"Dames assises sur des chaises."
              }
            },
            {
              id:3,
              image:{
                source:"/images/photos/danseurs-1.jpg",
                alt:"Danseurs en tenues traditionnelles."
              }
              
            } 
          ]
        }
      ]
        
    }

  },
}
</script>

<template>
  <div id="home">
    <div id="main-window">
      <section id="defilement-photos">
        <carousel :id="this.carousels[0].id" :setOfSlides="this.carousels[0].setOfSlides">
        </carousel>
      </section>
    </div>
  </div>
</template>

<style lang="scss">
#home {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
body{
  margin: 0px;
}
</style>