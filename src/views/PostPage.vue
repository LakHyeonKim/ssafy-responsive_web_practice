<template>
  <div>
    <header>
      <NavigationBar v-if="visialbe"></NavigationBar>
      <NavigationBarMobile v-if="!visialbe"></NavigationBarMobile>
    </header>
    <ImgBanner
      imgSrc="https://imboldn.com/wp-content/uploads/2019/04/Avengers-endgame-2019-02-08.jpg"
    >
      <div
        style="line-height:1.2em; font-size:1.2em; margin-left:45px"
        slot="text"
      >
        Post
      </div>
    </ImgBanner>
    <v-container>
      <!-- Post -->
      <v-layout>
        <v-row v-resize="onResize" align="center" justify="center">
          <v-flex xs12>
            <div class="post-center">
              <PostList :limits="6" :load-more="true"></PostList>
            </div>
          </v-flex>
        </v-row>
      </v-layout>
    </v-container>
    <Footer></Footer>
  </div>
</template>

<script>
import ImgBanner from '../components/ImgBanner'
import PostList from '../components/PostList'
import NavigationBar from '../components/NavigationBar'
import NavigationBarMobile from '../components/NavigationBarMobile'
import Footer from '../components/Footer'

export default {
  name: 'PostPage',
  data: () => ({
    visialbe: false
  }),
  components: {
    ImgBanner,
    PostList,
    NavigationBar,
    NavigationBarMobile,
    Footer
  },
  methods: {
    onResize () {
      if (window.innerWidth <= 576) {
        this.visialbe = false
      } else {
        this.visialbe = true
      }
    }
  },
  mounted () {
    this.onResize()
  }
}
</script>

<style>
.post-center {
  padding: 40px;
  text-align: center;
}
</style>
