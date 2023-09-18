<!--<template>-->
<!--  <div class="app-container documentation-container">-->
<!--    <a class="document-btn" target="_blank" href="https://store.akveo.com/products/vue-java-admin-dashboard-spring?utm_campaign=akveo_store-Vue-Vue_demo%2Fgithub&utm_source=vue_admin&utm_medium=referral&utm_content=demo_English_button">Java backend integration</a>-->
<!--    <a class="document-btn" target="_blank" href="https://panjiachen.github.io/vue-element-admin-site/">Documentation</a>-->
<!--    <a class="document-btn" target="_blank" href="https://github.com/PanJiaChen/vue-element-admin/">Github Repository</a>-->
<!--    <a class="document-btn" target="_blank" href="https://panjiachen.gitee.io/vue-element-admin-site/zh/">国内文档</a>-->
<!--    <dropdown-menu class="document-btn" :items="articleList" title="系列文章" />-->
<!--    <a class="document-btn" target="_blank" href="https://panjiachen.github.io/vue-element-admin-site/zh/job/">内推招聘</a>-->
<!--  </div>-->
<!--</template>-->

<!--<script>-->
<!--import DropdownMenu from '@/components/Share/DropdownMenu'-->

<!--export default {-->
<!--  name: 'Documentation',-->
<!--  components: { DropdownMenu },-->
<!--  data() {-->
<!--    return {-->
<!--      articleList: [-->
<!--        { title: '基础篇', href: 'https://juejin.im/post/59097cd7a22b9d0065fb61d2' },-->
<!--        { title: '登录权限篇', href: 'https://juejin.im/post/591aa14f570c35006961acac' },-->
<!--        { title: '实战篇', href: 'https://juejin.im/post/593121aa0ce4630057f70d35' },-->
<!--        { title: 'vue-admin-template 篇', href: 'https://juejin.im/post/595b4d776fb9a06bbe7dba56' },-->
<!--        { title: 'v4.0 篇', href: 'https://juejin.im/post/5c92ff94f265da6128275a85' },-->
<!--        { title: '自行封装 component', href: 'https://segmentfault.com/a/1190000009090836' },-->
<!--        { title: '优雅的使用 icon', href: 'https://juejin.im/post/59bb864b5188257e7a427c09' },-->
<!--        { title: 'webpack4（上）', href: 'https://juejin.im/post/59bb864b5188257e7a427c09' },-->
<!--        { title: 'webpack4（下）', href: 'https://juejin.im/post/5b5d6d6f6fb9a04fea58aabc' }-->
<!--      ]-->
<!--    }-->
<!--  }-->
<!--}-->
<!--</script>-->

<!--<style lang="scss" scoped>-->
<!--.documentation-container {-->
<!--  margin: 50px;-->
<!--  display: flex;-->
<!--  flex-wrap: wrap;-->
<!--  justify-content: flex-start;-->

<!--  .document-btn {-->
<!--    flex-shrink: 0;-->
<!--    display: block;-->
<!--    cursor: pointer;-->
<!--    background: black;-->
<!--    color: white;-->
<!--    height: 60px;-->
<!--    padding: 0 16px;-->
<!--    margin: 16px;-->
<!--    line-height: 60px;-->
<!--    font-size: 20px;-->
<!--    text-align: center;-->
<!--  }-->
<!--}-->
<!--</style>-->

<template>
  <div class="music-player">
    <div class="title-bar">
      <h1>{{ currentSong.title }}</h1>
      <button @click="playPause">播放</button>
    </div>
    <div class="controls">
      <button @click="previousSong">上一首</button>
      <button @click="nextSong">下一首</button>
      <button @click="playPause">暂停</button>
    </div>
    <div class="player">
      <audio :src="currentSong.src" @ended="nextSong"></audio>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      songs: [
        { title: '歌曲1', src: '/path/to/song1.mp3', album: '专辑1', releaseDate: '2022-01-01' },
        { title: '歌曲2', src: '/path/to/song2.mp3', album: '专辑2', releaseDate: '2022-02-01' },
        // ... 更多歌曲信息
      ],
      currentIndex: 0,
    };
  },
  computed: {
    currentSong() {
      return this.songs[this.currentIndex];
    },
  },
  methods: {
    playPause() {
      const audio = document.querySelector('audio')
      if (audio.paused) {
        audio.play();
      } else {
        audio.pause();
      }
    },
    previousSong() {
      this.currentIndex--;
      if (this.currentIndex < 0) {
        this.currentIndex = this.songs.length - 1;
      }
    },
    nextSong() {
      this.currentIndex++;
      if (this.currentIndex >= this.songs.length) {
        this.currentIndex = 0;
      }
    },
  },
};
</script>
