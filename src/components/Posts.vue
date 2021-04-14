<template>
  <div class="postsContainer">
    <Loader class="pageLoader" v-if="posts.length === 0"/>

    <Postcard v-for="post in posts" :key="post.postId"
              :image-src="post.photoUrl"
              :image-desc="post.photoDescription"
              :views-count="post.viewsCount"
              :username="post.username"
              :post-date="post.postDate"
    />

    <Loader v-if="posts.length > 0" class="contentLoader"/>
  </div>
</template>

<script>
import Postcard from './Postcard';
import Loader from './Loader';
import Carousel from './Carousel';
import axios from 'axios';
import debounce from 'lodash.debounce';


const mockImages = [
  require('../assets/img/mockup1.jpg'),
  require('../assets/img/mockup2.jpg'),
  require('../assets/img/mockup3.jpg'),
  require('../assets/img/mockup4.jpg'),
  require('../assets/img/mockup5.jpg'),
  require('../assets/img/mockup6.jpg'),
  require('../assets/img/mockup7.jpg'),
  require('../assets/img/mockup8.jpg'),
  require('../assets/img/mockup9.jpg'),
  require('../assets/img/mockup10.jpg'),
  require('../assets/img/mockup11.jpg'),
  require('../assets/img/mockup12.jpg'),
  require('../assets/img/mockup13.jpg'),
  require('../assets/img/mockup14.jpg'),
  require('../assets/img/mockup15.jpg')
];

const ANYCORS = 'https://cors-anywhere.herokuapp.com/';
const POSTAMOUNT = 3;

export default {
  name: 'Posts',
  components: {
    Postcard,
    Loader,
    Carousel
  },
  data() {
    return {
      posts: [],
      names: [
          'Maciej Miecz',
          'Przemek Mulik',
          'Dawid Mleczyk',
          'Kamil Piękniś'
      ]
    }
  },
  mounted() {
    this.loadMorePosts();
    window.addEventListener('scroll', debounce(this.handleScroll, 100));
  },
  methods: {
    loadMorePosts() {
      axios.get('https://baconipsum.com/api/?type=meat-and-filler?paras=' + POSTAMOUNT).then((res) => {
        for (let i = 0; i < POSTAMOUNT; i++) {
          this.posts.push(
              {
                "postId": this.posts.length,
                "viewsCount": Math.floor(Math.random() * 2000),
                "username": this.names[Math.floor(Math.random() * this.names.length)],
                "photoUrl": this.generateImageSources(),
                "photoDescription": res.data[i],
                "postDate": new Date().toLocaleDateString()
              }
          )
        }
      });
    },
    handleScroll() {
      let distanceFromBottom = document.body.scrollHeight - window.innerHeight - window.scrollY;
      if (distanceFromBottom < 450) {
        this.loadMorePosts();
      }
    },
    // temp solution
    generateImageSources() {
      let imgArray = [];

      for (let i = 0; i <= Math.round(Math.random() * 4); i++) {
        imgArray.push(mockImages[Math.floor(Math.random() * mockImages.length)]);
      }

      return imgArray;
    }
  }
}
</script>

<style scoped lang="scss">
@import "../assets/scss/theme.scss";

.postsContainer {
  max-width: $mobileBreakpoint;
  margin: 0 auto;

  @media (min-width: $mobileBreakpoint) {
    padding-top: 80px;
  }
}

.pageLoader {
  position: absolute;
  transform: translate(-50%, -50%);
  top: 55%;
  left: 50%;
}

.contentLoader {
  transform: scale(.5) translateY(-20%);
}
</style>
