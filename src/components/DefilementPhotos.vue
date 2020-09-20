<script>
    import ElementPhoto from "./ElementPhoto.vue"

    export default {
        name:"DefilementPhotos",
        components:{
            ElementPhoto
        },
        data() {
            return {
                
            }
        }
    }
</script>

<template>
    <section id="defilement-photos">
        <ElementPhoto :photo="image.source"/>
    </section>
</template>

<style lang="scss" scoped>
    #defilement-photos{
        display: flex;
        flex-direction: column;
    }
</style>