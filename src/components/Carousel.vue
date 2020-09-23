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
            directionSlide:null
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
        goTo (i) {
            this.directionSlide = this.index < i ? 'right' : 'left';
            this.index = i;
        }
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
        <div class="slide-index">
            <button v-for="n in this.slidesCount" :key="n" @click="goTo(n-1)" :class="{active:n-1 == index}"></button>  
        </div>

    </div>
</template>
<style lang="scss" scoped>

    .slide-index{
        position: absolute;
        top:50px;
        left: 0;
        right: 0;
        text-align: center;
        button{
            width: 12px;
            height: 12px;
            background-color: white;
            mix-blend-mode: difference;
            border: none;
            border-radius: 100%;
            margin:10px;
            padding: 0;
            cursor: pointer;

            transition: all 0.5s;
        }
        button.active{
            transform: scale(1.4);
            margin: 10px 20px;

        }
    }


    .carousel-slide-container{
        position: relative;
        width: 100%;
        height: 100%;
        bottom:0;
        overflow: hidden;
    }
    .carousel-nav{
        position: absolute;
        border:none;
        cursor: pointer;
        top:50%;
        height:80px;
        width:80px;
        background-repeat: no-repeat;
        background-size: contain;
        background-color: transparent;
        mix-blend-mode: exclusion;
        transition: transform 0.4s;
    }
    .carousel-nav:hover{
        transform: scale(1.3);
    }
    .carousel-nav-prev{
        left:150px;
        background-image: url("/images/icons/keyboard_arrow_left-white-18dp.svg");
    }
    .carousel-nav-next{
        right:100px;
        background-image: url("/images/icons/keyboard_arrow_right-white-18dp.svg");
    }

</style>

