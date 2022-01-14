<template>
  <section class="section">
    <div class="title"> <h2><span>/</span>Reviews</h2></div>
    <div class="section-center">
      <People :people="peopleData" :index="index" v-model="index"/>
      <Button />
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
      index: 0
    }
  },

  methods: {
    // nextSlide () {
    //   function setNextIndex() {
    //     let index = this.index + 1
    //     if(index < this.peopleData.length - 1) {
    //       index = 0
    //     }
    //     return index
    //   }
    //   this.index = setNextIndex()
    // },

    afterSlide () {
      let index = this.index + 1
      if (index < this.peopleData.length - 1){
        index = 0
      }
      this.index = index
    },

    // prevSlide() {
    //   function setIndex() {
    //     let index = this.index - 1
    //     if(index < 0){
    //       index = this.peopleData.length - 1
    //     }
    //     return index
    //   }
    //   this.index = setIndex()
    // },

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

  computed () {},

  watch() {
    "index", function () {
      this.setSlider()
    }
    console.log(this.index)
  },
}
</script>

<style src="./assets/index.css">
</style>
