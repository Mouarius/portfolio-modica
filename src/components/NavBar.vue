<script>
    export default {
        name:"NavBar"
    }
</script>

<template>
    <nav id="nav-bar">
        <a href="#"><img class="menu-icon" src="/images/icons/menu-white-18dp.svg" alt="menu"></a>
        <a href="#"><img class="menu-icon" src="/images/icons/person-white-18dp.svg" alt="contact"></a>

    </nav>
</template>

<style lang="scss" scoped>
    nav{
        background-color: black;

        width: 80px;
        height: 100%;
        top: 0;
        left: 0;

        display: flex;
        flex-direction: column;

        position: fixed;

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

</style>