<script>
    import CarouselSlide from "../components/CarouselSlide.vue"

    export default {
    name:"Carousel",
    components:{
        CarouselSlide
    },
    props:["id","setOfSlides"],
    data (){
        return{
            index:0,
            slides:[],
        }
    },
    mounted (){
        this.slides = this.$children
        this.slides.forEach((slide, i) => {
            slide.index = i
        })
    },
    computed:{
        slidesCount(){
            return this.slides.length
        }
    },
    methods:{
        nextSlide () {
            if (this.index < this.slidesCount -1){
                this.index +=1
            }
            else{
                this.index = 0
            }
        },
        prevSlide () {
            if (this.index > 0){
                this.index -=1
            }
            else{
                this.index = this.slidesCount - 1
            }
        },
    }
    }
</script>

<template>
    <div class="global-carousel">
        <div class="carousel-slide-container">
                <carousel-slide 
                v-for="slide in setOfSlides"
                v-bind:key="slide.id"
                v-bind:image="slide.image"
                ></carousel-slide>
        </div>
            
        Index carousel : {{ index }}
        <button class="carousel-prev carousel-nav" v-on:click="prevSlide">Précédent</button>
        <button class="carousel-next carousel-nav" v-on:click="nextSlide">Suivant</button>

    </div>
</template>
<style lang="scss" scoped>
    .carousel-slide-container{
        display: flex;
        flex-direction: row;
        margin: 0;
        padding: 0;
    }
</style>

