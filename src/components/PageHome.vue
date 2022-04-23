<template>
  <div  v-for="thread in threads"
        :key="thread.id"
        class="col-large push-top">

<!--    <ul class="breadcrumbs">-->
<!--      <li><a href="#"><i class="fa fa-home fa-btn"></i>Home</a></li>-->
<!--      <li><a href="category.html">Discussions</a></li>-->
<!--      <li class="active"><a href="#">Cooking</a></li>-->
<!--    </ul>-->

    <div class="post-list">
      <div class="post" v-for="postId in thread.posts" :key="postId">

        <div class="user-info">
          <a href="#" class="user-name">{{ userById(postById(postId).userId).name }}</a>

          <a href="#">
            <img class="avatar-large" :src="userById(postById(postId).userId).avatar" alt="">
          </a>

          <p class="desktop-only text-small">107 posts</p>

        </div>

        <div class="post-content">
          <div>
            <p>{{ postById(postId).text }}</p>
          </div>
        </div>

        <div class="post-date text-faded">
          <p>{{ postById(postId).publishedAt }}</p>
        </div>
      </div>
    </div>
  </div>

<!--  <div>Hello from page home</div>-->
<!--  <div v-for="thread in threads" :key="thread.id">-->
<!--    <h2>{{ thread.title }}</h2>-->
<!--    <div v-for="postId in thread.posts" :key="postId">-->
<!--      <p>{{ userById(postById(postId).userId).name }}</p>-->
<!--      <p>{{ postById(postId).text }}</p>-->
<!--    </div>-->
<!--  </div>-->
</template>

<script>
import sourceData from '@/data.json'
export default {
  name: "PageHome",
  data () {
    return {
      threads: sourceData.threads,
      posts: sourceData.posts,
      users: sourceData.users
    }
  },
  methods: {
    postById(postId) {
      return this.posts.find(p => p.id === postId)
    },
    userById(userId) {
      return this.users.find(p => p.id === userId)
    },
  }
}
</script>

<style scoped>

</style>
