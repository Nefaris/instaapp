<template>
    <div class="carouselWrapper">
        <div class="swiper-container">
            <img class="multiplePhotosIcon" src="../assets/img/layer-group-solid.svg" alt=""/>
            <div class="swiper-wrapper">
                <div class="swiper-slide" v-for="image of imagesArray">
                    <img :src="image" alt=""/>
                </div>
            </div>
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
        mounted() {
            new Swiper('.swiper-container', {
                autoHeight: true
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