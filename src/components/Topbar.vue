<template>
    <div class="topbar">
        <div class="innerBar">
            <img class="logo" src="../assets/img/logo.png" alt="">
        </div>
    </div>
</template>

<script>
    export default {
        name: "Topbar"
    }
</script>

<style scoped lang="scss">
    @import "../assets/scss/theme.scss";

    .topbar {
        position: sticky;
        top: 0;
        left: 0;
        z-index: 999;
        height: 50px;
        width: 100%;
        padding: 10px 20px;
        box-shadow: 0 2px 5px 0 rgba(0, 0, 0, 0.25);
        background-color: $backgroundLight;
        display: flex;
        justify-content: center;
        align-items: center;

        @media (min-width: $mobileBreakpoint) {
            background-color: #ffffff;
            padding: 10px 0;
        }
    }

    .innerBar {
        max-width: $mobileBreakpoint;
        width: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .accountSettingIcon {
        max-height: 16px;
        cursor: pointer;
    }

    .logo {
        max-height: 26px;
    }
</style>