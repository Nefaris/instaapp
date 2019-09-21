<template>
    <div class="carouselWrapper">
        <div class="swiper-container" :class="swiperId">
            <img class="multiplePhotosIcon" src="../assets/img/layer-group-solid.svg" alt=""/>
            <div class="swiper-wrapper">
                <div class="swiper-slide" v-for="image of imagesArray">
                    <img :src="image" alt=""/>
                </div>
            </div>
            <div class="swiper-pagination"></div>
        </div>
    </div>
</template>

<script>
    import Swiper from 'swiper';

    export default {
        name: "Carousel",
        props: {
            imagesArray: Array
        },
        data() {
            return {
                swiperId: "",
            }
        },
        created() {
            this.swiperId = "swiper-container-" + Date.now();
        },
        mounted() {
            const swiperClass = '.' + this.swiperId;
            new Swiper(swiperClass, {
                autoHeight: true,
                mousewheel: true,
                pagination: {
                    el: '.swiper-pagination',
                }
            });
        }
    }
</script>

<style lang="scss">
    @import "../assets/css/swiper.min.css";

    .swiper-pagination-bullet-active {
        background: #42b783;
    }

    .swiper-container-horizontal > .swiper-pagination-bullets {
        bottom: 20px;
    }

    .swiper-slide {
        height: 100%;

        img {
            max-width: 100%;
        }
    }

    .multiplePhotosIcon {
        position: absolute;
        top: 20px;
        right: 20px;
        z-index: 2;
        width: 26px;
        opacity: .75;
    }
</style>