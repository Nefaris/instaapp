<template>
    <div class="home">
        <Topbar/>
        <Posts/>
    </div>
</template>

<script>
    import Topbar from "../components/Topbar";
    import Posts from "../components/Posts";

    export default {
        name: 'home',
        components: {
            Topbar,
            Posts
        }
    }
</script>

<style scoped lang="scss">

</style>
