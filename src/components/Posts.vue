<template>
    <div class="postsContainer">
        <Loader v-if="posts.length === 0"/>
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
    import Loader from "./Loader";
    import axios from 'axios';
    import debounce from 'lodash.debounce';


    const mockImages = [
        require("../assets/dolomites-4342531_640.jpg"),
        require("../assets/mount-st-helens-164848_640.jpg"),
        require("../assets/mountaineer-2080138_640.jpg"),
        require("../assets/thunderstorm-3440450_640.jpg"),
        require("../assets/waterfall-2227010_640.jpg"),
        require("../assets/dolomites-4342531_640.jpg"),
        require("../assets/mount-st-helens-164848_640.jpg"),
        require("../assets/sheep-4474683_640.jpg"),
        require("../assets/sunrise-4473359_640.jpg"),
        require("../assets/way-4459666_640.jpg"),
    ];

    const ANYCORS = "https://cors-anywhere.herokuapp.com/";
    const POSTAMOUNT = 10;

    export default {
        name: "Posts",
        components: {
            Postcard,
            Loader
        },
        mounted() {
            // just to see nice page loader
            setTimeout(() => {
                this.loadMorePosts();
                window.addEventListener('scroll', debounce(this.handleScroll, 200));
            }, 3000);
        },
        data() {
            return {
                posts: []
            }
        },
        methods: {
            loadMorePosts() {
                axios.all([
                    axios.get('https://baconipsum.com/api/?type=meat-and-filler?paras=' + POSTAMOUNT),
                    axios.get(ANYCORS + "https://uinames.com/api?amount=" + POSTAMOUNT)
                ]).then(axios.spread((loremRes, nameRes) => {
                    for (let i = 0; i < POSTAMOUNT; i++) {
                        this.posts.push(
                            {
                                "postId": this.posts.length,
                                "viewsCount": Math.floor(Math.random() * 2000),
                                "username": nameRes.data[i].name + " " + nameRes.data[i].surname,
                                "photoUrl": mockImages[Math.floor(Math.random() * mockImages.length)],
                                "photoDescription": loremRes.data[i]
                            }
                        )
                    }
                }));
            },
            handleScroll() {
                let distanceFromBottom = document.body.scrollHeight - window.innerHeight - window.scrollY;
                if (distanceFromBottom < 300) {
                    this.loadMorePosts();
                }
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