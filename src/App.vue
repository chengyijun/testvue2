<template>
    <div id="app">
        <h1>这里是app</h1>
        <p>app的内容</p>
        <home-swiper id="sw"></home-swiper>
    </div>
</template>

<script>
    import HomeSwiper from "@/views/HomeSwiper";

    export default {
        name: 'app',
        components: {
            HomeSwiper
        }
    }
</script>

<style>

</style>
