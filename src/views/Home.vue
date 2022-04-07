<template>
  <div class="home">Helloooo</div>
  <p ref="para">My name is {{ name }} and my age is {{ age }}</p>
  <button @click="handleClick">click meeee</button>
  <button @click="age++">Click me to see me age</button>
  <input type="text" v-model="name" />
</template>

<script>
import { ref } from 'vue'

export default {
  name: 'Home',

  setup() {
    /* by default, are not reactive variables:
    let name = 'mario'
    let age = 30 */

    const name = ref('mario')
    const age = ref(30)

    const handleClick = () => {
      name.value = 'luigi'
      age.value = 42
    }

    return {
      name: name,
      age: age,
      handleClick,
    }
  },
}
</script>
