<template>
  <section class="section">
    <div class="title"> <h2><span>/</span>Reviews</h2></div>
    <div class="section-center">
      <People :people="peopleData" :index="index"/>
      <Button v-on:previous-slide="previousSlide" v-on:next-slide="afterSlide" />
    </div>
  </section>
</template>

<script>
import data from './components/data'
import People from './components/People.vue'
import Button from './components/Button.vue'
export default {
  name: 'App',
  components: {
    People,
    Button,
  },
  data() {
    return {
      peopleData: data,
      index: 0,
    }
  },

  methods: {
    afterSlide () {
      let index = this.index + 1
      if (index > this.peopleData.length - 1){
        index = 0
      }
      this.index = index
    },


    previousSlide () {
      let index = this.index - 1
      if (index < 0) {
        index = this.peopleData.length - 1
      }
      this.index = index
    },

    setSlider () {
      let slider =  setInterval(() => {
        this.afterSlide()
      }, 5000)
      return() => {
        clearInterval(slider)
      }
    }
  },

  updated () {},

}
</script>

<style src="./assets/index.css">
</style>
