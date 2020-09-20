<script>
export default {
    name:"ElementPhoto",
    props:["image"],
    data (){
        return{
            
        }
    }
}
</script>

<template>
    <div class="element-photo">
        <img v-bind:src="image.source" :alt="image.alt" />
    </div>
</template>

<style lang="scss" scoped>
    .element-photo{
        img{
            width:100%;
        }
    }
    
</style>