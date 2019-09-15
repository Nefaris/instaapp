<template>
    <div class="topbar">
        <img src="../assets/img/logo.png" alt="">
    </div>
</template>

<script>
    export default {
        name: "Topbar"
    }
</script>

<style scoped lang="scss">
    .topbar {
        position: fixed;
        top: 0;
        left: 0;
        height: 46px;
        width: 100%;
        padding: 10px 0;
        /*border-bottom: 1px solid rgba(0, 0, 0, .0975);*/
        box-shadow: 0 2px 5px 0 rgba(0, 0, 0, 0.25);
        background-color: #fafafa;
        display: flex;
        justify-content: center;
        align-items: center;

        @media (min-width: 600px) {
            background-color: #ffffff;
        }
    }

    img {
        max-height: 26px;
    }
</style>