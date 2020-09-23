<script>
export default {
    name:"CarouselSlide",
    props:["image"],
    data () {
        return{
            index: 0,
            indexVisible: false,
        }
    },
    computed: {
        isVisible() {
            return this.index === this.$parent.index
        },
        slideDirection(){
            if(this.$parent.directionSlide)
            {
                return "slide-" + this.$parent.directionSlide //crée la classe du nom de transition en fonction de la propriété directionSlide du parent
            }
            return ""
        }
    },
    methods:{

    }
}
</script>

<template>
    <transition :name="slideDirection">
        <div v-show="isVisible" class="carousel-slide">
            <img class="carousel-slide-image" v-bind:src="image.source" v-bind:alt="image.alt"/>
        </div>
    </transition>
</template>
<style lang="scss" scoped>

    .carousel-slide img{
        width: 100%;
    }

    // Durée des transitions
    .slide-left-enter-active, .slide-left-leave-active,.slide-right-enter-active, .slide-right-leave-active
    {
        transition: all 1.5s;
    }
    /*--- [DEBUT] TRANSITION DROITE ---*/
    .slide-right-leave-active{
        position: absolute;
        top:0;
        left:0;
        right:0;
        width:100%;
    }
    .slide-right-enter
    {
        transform:translateX(100%);
    }
    .slide-right-leave-to
    {
        transform: translateX(-100%);
    }
    /*--- [FIN] TRANSITION DROITE ---*/
    /*--- [DEBUT] TRANSITION GAUCHE ---*/
    .slide-left-leave-active{
        position: absolute;
        top:0;
        left:0;
        right:0;
        width:100%;
    }
    .slide-left-enter
    {
        transform:translateX(-100%);
    }
    .slide-left-leave-to
    {
        transform: translateX(100%);
    }
    /*--- [FIN] TRANSITION GAUCHE ---*/

</style>