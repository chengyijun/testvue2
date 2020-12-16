<template>
    <swiper>
        <swiper-item v-for="(item, id) in banners" :key="id">
            <a href="###">
                <img :src="item.image" alt="">
            </a>
        </swiper-item>
    </swiper>
</template>

<script>
    import {Swiper, SwiperItem} from "../components/swiper/index"

    export default {
        name: "HomeSwiper",
        props: {
            banners: {
                type: Array,
                default() {
                    return [
                        {
                            image: require("../../public/imgs/1.png")
                        },
                        {
                            image: require("../../public/imgs/2.png")
                        },
                        {
                            image: require("../../public/imgs/3.png")
                        }

                    ]
                }
            }
        },
        components: {
            Swiper,
            SwiperItem
        }
    }
</script>

<style scoped>

</style>
