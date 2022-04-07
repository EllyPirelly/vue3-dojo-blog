<template>
  <div class="home">
    <h1>Home</h1>
    <input type="text" v-model="search" />
    <p>search term - {{ search }}</p>
    <div v-for="name in matchingNames" :key="name">{{ name }}</div>
  </div>
  <button @click="handleClick">stop watching</button>
</template>

<script>
import { computed, ref, watch, watchEffect } from 'vue'

export default {
  name: 'Home',

  setup() {
    const search = ref('')
    const names = ref([
      'mario',
      'yoshi',
      'luigi',
      'toad',
      'bowser',
      'koopa',
      'peach',
    ])

    const stopWatch = watch(search, () => {
      console.log('watch function')
    })

    /* always runs initially */
    const stopEffect = watchEffect(() => {
      console.log('watchEffect function', search.value)
    })

    const handleClick = () => {
      stopWatch()
      stopEffect()
    }

    const matchingNames = computed(() => {
      return names.value.filter((name) => name.includes(search.value))
    })

    return {
      search,
      names,
      matchingNames,
      handleClick,
    }
  },
}
</script>
