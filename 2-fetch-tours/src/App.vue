<template>
  <div>
    <Tours />
  </div>
</template>

<script>
import Tours from './components/Tours'

const url = 'https://course-api.com/react-tours-project'
console.log(url)

export default {
  name: 'App',
  components: {
    Tours
  }
}
</script>

<style src="./assets/index.css" scoped>

</style>
