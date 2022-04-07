<template>
  <div class="home">
    <h1>Home</h1>

    <h2>Refs</h2>
    <p>
      {{ ninjaOne.name }} - {{ ninjaOne.age }} - with ref: {{ nameOne.name }}
    </p>
    <button @click="updateNinjaOne">update ninja one</button>

    <h2>Reactive</h2>
    <p>
      {{ ninjaTwo.name }} - {{ ninjaTwo.age }} - with reactive: {{ nameTwo }}
    </p>
    <button @click="updateNinjaTwo">update ninja two</button>
  </div>
</template>

<script>
import { ref, reactive } from 'vue'

export default {
  name: 'Home',

  setup() {
    /* ref versus reactive */
    const ninjaOne = ref({ name: 'mario', age: 30 })
    const ninjaTwo = reactive({ name: 'luigi', age: 42 })

    const nameOne = ref({ name: 'mario' })
    /* we can't use primitive values with reactive() */
    let nameTwo = reactive('luigi')

    const updateNinjaOne = () => {
      ninjaOne.value.name = 'Marianne'
      ninjaOne.value.age = 2200
      nameOne.value.name = 'Mary'
    }

    const updateNinjaTwo = () => {
      ninjaTwo.name = 'Luanne'
      ninjaTwo.age = 3200
      /* won't work because it's a primitive value and not reactive */
      nameTwo = 'LuAnne'
    }

    return {
      ninjaOne,
      updateNinjaOne,
      ninjaTwo,
      updateNinjaTwo,
      nameOne,
      nameTwo,
    }
  },
}
</script>
