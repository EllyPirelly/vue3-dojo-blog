<template>
  <div class="post-list">
    <div v-for="post in posts" :key="post.id">
      <SinglePost :post="post" />
    </div>
  </div>
</template>

<script>
import SinglePost from './SinglePost.vue'
import { onMounted, onUnmounted, onUpdated } from 'vue'

export default {
  props: ['posts'],

  components: {
    SinglePost,
  },

  setup(props) {
    console.log(props.posts)

    // lifecycle hooks inside of the setup function
    onMounted(() => console.log('component mounted'))
    onUnmounted(() => console.log('component unmounted'))
    onUpdated(() => console.log('component updated'))
  },

  // mounted using options API
  mounted() {
    console.log('outside of setup using options API')
  },
}
</script>

<style lang="scss">
//
</style>
