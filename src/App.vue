<template>
    <div id="app">
        <div id="nav">
            <!--      <router-link to="/">Home</router-link> |-->
            <!--      <router-link to="/about">About</router-link>-->
        </div>
        <router-view/>
    </div>
</template>

<style lang="scss">
    @import "assets/scss/theme.scss";

    *,
    *::before,
    *::after {
        box-sizing: border-box;
    }

    body {
        margin: 0;
        padding: 0;
        background-color: $backgroundWhite;
        overflow-x: hidden;

        @media (min-width: 600px) {
            background-color: $backgroundLight;
        }
    }

    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
    }

    ::-webkit-scrollbar {
        width: 12px;
    }

    ::-webkit-scrollbar-button {
        width: 0;
        height: 0;
    }

    ::-webkit-scrollbar-thumb {
        background-color: #000000;
        border: solid 4px $backgroundLight;
        border-radius: 15px;
    }

    ::-webkit-scrollbar-thumb:hover {
        background-color: #000000;
    }

    ::-webkit-scrollbar-thumb:active {
        background-color: #000000;
    }

    ::-webkit-scrollbar-track {
        background-color: transparent;
        border-radius: 50px;
    }

    ::-webkit-scrollbar-track:hover {
        background-color: transparent;
    }

    ::-webkit-scrollbar-track:active {
        background-color: transparent;
    }

    ::-webkit-scrollbar-corner {
        background-color: transparent;
    }

    /*#nav {*/
    /*    padding: 30px;*/

    /*    a {*/
    /*        font-weight: bold;*/
    /*        color: #2c3e50;*/

    /*        &.router-link-exact-active {*/
    /*            color: #42b983;*/
    /*        }*/
    /*    }*/
    /*}*/
</style>
