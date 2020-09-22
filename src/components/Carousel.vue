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
            directionSlide:'right'
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
            this.directionSlide = 'right'
            if (this.index < this.slidesCount -1){
                this.index +=1
            }
            else{
                this.index = 0
            }
        },
        prevSlide () {
            this.directionSlide = 'left'
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
        <button class="carousel-nav-prev carousel-nav" v-on:click="prevSlide"></button>
        <button class="carousel-nav-next carousel-nav" v-on:click="nextSlide"></button>

    </div>
</template>
<style lang="scss" scoped>
    .carousel-slide-container{
        position: relative;
        width: 100%;
        height: 100%;
        bottom:0;
    }
    .carousel-nav{
        position: absolute;
        border:none;
        cursor: pointer;
        top:50%;
        background-repeat: no-repeat;
        background-size: contain;
        background-color: transparent;
        mix-blend-mode: difference;
        transition: transform 0.4s;
    }
    .carousel-nav:hover{
        transform: scale(1.3);
    }
    .carousel-nav-prev{
        left:150px;
        height:50px;
        width:50px;
        background-image: url("/images/icons/keyboard_arrow_left-white-18dp.svg");
    }
    .carousel-nav-next{
        right:100px;
        height:50px;
        width:50px;
        background-image: url("/images/icons/keyboard_arrow_right-white-18dp.svg");
    }

</style>

