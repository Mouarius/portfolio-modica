<script>
export default {
    name:"CarouselSlide",
    props:["image"],
    data () {
        return{
            index: 0,
            indexVisible: false
        }
    },
    computed: {
        isVisible() {
            // return this.index === this.$parent.index
            return true
        }
    }
}
</script>

<template>
    <transition name="slide-fade">
        <div v-show="isVisible" class="carousel-slide">
            <span class="slide-index" v-if="this.indexVisible">{{ index }}</span>
            <img class="carousel-slide-image" v-bind:src="image.source" v-bind:alt="image.alt"/>
        </div>
    </transition>
</template>
<style lang="scss" scoped>
    .carousel-slide{
        img{
            height:500px;
        }
    }
    .slide-index{
        display: block;
        position:relative;
    }
    .slide-fade-enter-active, .slide-fade-leave-active
    {
        transition: all 5s;
    }
    .slide-fade-enter
    {
        transform: translateX(2000px);
    }
    .slide-fade-leave-to
    {
        transform: translateX(-2000px);
    }
</style>