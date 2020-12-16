<template>
    <div id="hy-swiper">
        <div class="swiper" @touchstart="touchStart" @touchmove="touchMove" @touchend="touchEnd" @touchmove.prevent>
            <slot></slot>
        </div>
        <slot name="indicator">
        </slot>
        <div class="indicator">
            <slot name="indicator" v-if="showIndicator && slideCount>1">
                <div v-for="(item, index) in slideCount" class="indi-item" :class="{active: index === currentIndex-1}"
                     :key="index"></div>
            </slot>
        </div>
    </div>
</template>

<script>

    import MySwiper from "@/components/swiper/myswiper";

    export default {
        name: "Swiper",
        props: {
            interval: {
                type: Number,
                default: 3000
            },
            animDuration: {
                type: Number,
                default: 300
            },
            moveRatio: {
                type: Number,
                default: 0.25
            },
            showIndicator: {
                type: Boolean,
                default: true
            }
        },
        data: function () {
            return {
                slideCount: 0, // 元素个数
                totalWidth: 0, // swiper的宽度
                swiperStyle: {}, // swiper样式
                currentIndex: 1, // 当前的index
                scrolling: false, // 是否正在滚动
            }
        },
        mounted: function () {
            const mySwiper = new MySwiper(this.interval, this.animDuration, this.moveRatio, this.showIndicator)
            this.sliCount = mySwiper.slideCount
            this.totalWidth = mySwiper.totalWidth
            this.swiperStyle = mySwiper.swiperStyle
            this.scrolling = mySwiper.scrolling
        },
        methods: {}
    }
</script>

<style scoped>
    #hy-swiper {
        overflow: hidden;
        position: relative;
    }

    .swiper {
        display: flex;
    }

    .indicator {
        display: flex;
        justify-content: center;
        position: absolute;
        width: 100%;
        bottom: 8px;
    }

    .indi-item {
        box-sizing: border-box;
        width: 8px;
        height: 8px;
        border-radius: 4px;
        background-color: #fff;
        line-height: 8px;
        text-align: center;
        font-size: 12px;
        margin: 0 5px;
    }

    .indi-item.active {
        background-color: rgba(212, 62, 46, 1.0);
    }
</style>
