<script>
    export default {
        name:"NavBar"
    }
</script>

<template>
    <nav id="nav-bar">
        <router-link to="/"><img class="menu-icon" src="/images/icons/menu-white-18dp.svg" alt="menu"></router-link>
        <router-link to="/contact"><img class="menu-icon" src="/images/icons/person-white-18dp.svg" alt="contact"></router-link>
    </nav>
</template>

<style lang="scss" scoped>
    nav{
        background-color: black;

        width: 80px;
        height: 100%;
        top: 0;
        left: -79px;

        display: flex;
        flex-direction: column;

        position: fixed;

        opacity:0;

        transition: transform 0.5s, opacity 0.5s;

        a{
            display: flex;

            width: 60px;
            height: 60px;

            margin: auto;
            margin-top: 10px;
            margin-bottom: 10px;


            .menu-icon{
                width:100%;
                height: 100%;
            }
        }
    }
    nav:hover{
        transform: translateX(79px);
        opacity:1;
    }

</style>