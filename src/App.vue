<template>
  <div class="row">
    <div class="col-md-4">
      <h1>Titles</h1>
      <div class="titles">
          <ul class="list-group">
          <li class="list-group-item" v-for="post in posts" :key="post.id">
            <a href="#" class="list-group-item-action"
                @click.prevent="selectPost(post)">
              {{post.title}}
            </a>
          </li>
        </ul>
      </div>
    </div>
    <div class="col-md-8">
      <Post :post="selectedPost" v-if="selectedPost!=null" />
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import Post from './components/Post.vue'
// import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    Post
  },
  data() {
    return {
      posts: [],
      selectedPost: null
    }
  },
  methods: {
    async getPosts() {
      await axios.get('https://jsonplaceholder.typicode.com/posts')
      .then(response => {
        if(response.status==200) {
          this.posts = response.data;
        }
      })
    },
    selectPost(post) {
      this.selectedPost = post
    }
  },
  created() {
    this.getPosts()
  }
}
</script>

<style>
.titles {
  height: 88vh;
  overflow: scroll;
}
</style>
