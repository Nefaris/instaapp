<template>
    <div class="eeee">
        <div class="swiper-container">
            <div class="swiper-wrapper">
                <div class="swiper-slide">
                    <img src="../assets/img/mockup1.jpg" alt=""/>
                </div>
                <div class="swiper-slide">
                    <img src="../assets/img/mockup2.jpg" alt=""/>
                </div>
                <div class="swiper-slide">
                    <img src="../assets/img/mockup3.jpg" alt=""/>
                </div>
                <div class="swiper-slide">
                    <img src="../assets/img/mockup4.jpg" alt=""/>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import Swiper from 'swiper';

    export default {
        name: "Postcardv2",
        mounted() {
            const mySwiper = new Swiper('.swiper-container');
        }
    }
</script>

<style scoped lang="scss">
    img {
        max-width: 100%;
    }
</style>