<template>
  <div class="home">
    <h1>home</h1>
    <div v-if="error">{{ error }}</div>
    <div v-if="posts.length" class="layout">
      <PostList :posts="posts" />
    </div>
    <div v-else>Loading...</div>
  </div>
</template>

<script>
import PostList from '../components/PostList.vue'
import getPosts from '../composables/getPosts'

export default {
  name: 'Home',

  components: {
    PostList,
  },

  setup() {
    const { posts, error, load } = getPosts()

    load()

    return {
      error,
      posts,
    }
  },
}
</script>

<style lang="scss">
.home {
  max-width: 1200px;
  margin: 0 auto;
  padding: 10px;
}

.layout {
  width: 100%;

  @media screen and (min-width: 768px) {
    /*     display: grid;
    grid-template-columns: 3fr 1fr;
    gap: 20px; */
  }
}
</style>
