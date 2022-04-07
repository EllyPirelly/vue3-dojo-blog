<template>
  <div class="home">Helloooo</div>
  <p ref="para">My name is {{ name }} and my age is {{ age }}</p>
  <button @click="handleClick">click meeee</button>
</template>

<script>
import { ref } from 'vue'

export default {
  name: 'Home',

  setup() {
    console.log(this)

    const para = ref(null)
    console.log('after declare: ', para, para.value) // still has the value of null!

    let name = 'mario'
    let age = 30

    const handleClick = () => {
      console.log('in handleClick: ', para, para.value)
      para.value.classList.add('test')
      para.value.textContent = 'this now is different on click'
    }

    return {
      name: name,
      age: age,
      handleClick,
      para,
    }
  },
}
</script>
