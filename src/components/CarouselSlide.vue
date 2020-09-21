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
            return this.index === this.$parent.index
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
    .carousel-slide img{
        width: 100%;
    }
    .slide-index{
        display: block;
        position:relative;
    }
    .slide-fade-enter-active, .slide-fade-leave-active
    {
        transition: all 1.5s;
    }
    .slide-fade-leave-active{
        position: absolute;
        top:0;
        left:0;
        right:0;
        width:100%;
    }
    .slide-fade-enter
    {
        transform:translateX(100%);
    }
    .slide-fade-leave-to
    {
        transform: translateX(-100%);
    }
</style>