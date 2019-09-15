<template>
    <div class="postsContainer">
        <Postcard v-for="post in posts" :key="post.postId"
                  :image-src="post.photoUrl"
                  :image-desc="post.photoDescription"
                  :views-count="post.viewsCount"
                  :username="post.username"
        />
    </div>
</template>

<script>
    import Postcard from "./Postcard";

    const mockImages = [
        require("../assets/dolomites-4342531_640.jpg"),
        require("../assets/mount-st-helens-164848_640.jpg"),
        require("../assets/mountaineer-2080138_640.jpg"),
        require("../assets/thunderstorm-3440450_640.jpg"),
        require("../assets/waterfall-2227010_640.jpg"),
    ];

    export default {
        name: "Posts",
        components: {
            Postcard
        },
        data() {
            return {
                posts: [
                    {
                        "postId": 0,
                        "viewsCount": 241,
                        "username": "Robert Wagner",
                        "photoUrl": mockImages[0],
                        "photoDescription": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat."
                    },
                    {
                        "postId": 1,
                        "viewsCount": 1241,
                        "username": "Brenda Foster",
                        "photoUrl": mockImages[1],
                        "photoDescription": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat."
                    },
                    {
                        "postId": 2,
                        "viewsCount": 21,
                        "username": "Roy Hill",
                        "photoUrl": mockImages[2],
                        "photoDescription": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat."
                    },
                    {
                        "postId": 3,
                        "viewsCount": 165,
                        "username": "Kathryn Davis",
                        "photoUrl": mockImages[3],
                        "photoDescription": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat."
                    },
                    {
                        "postId": 4,
                        "viewsCount": 1165,
                        "username": "John Doe",
                        "photoUrl": mockImages[4],
                        "photoDescription": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat."
                    }
                ]
            }
        }
    }
</script>

<style scoped lang="scss">
    .postsContainer {
        padding-top: 46px;
        max-width: 600px;
        margin: 0 auto;

        @media (min-width: 600px) {
            padding-top: 120px;
        }
    }
</style>