<template>
  <section class="section-center">
    <h3>Tired of boring lorem ipsum?</h3>

    <form class="lorem-form" @submit.prevent="handleSubmit">
      <label htmlFor="amount">Paragraphs</label>
      <input type="number" v-model="count">
      <button class="btn" type="submit">generate</button>
    </form>
    <article class="lorem-text" v-for="(text, index) in text"  :key="index">
      <p>{{text}}</p>
    </article>
  </section>
</template>

<script>
import data from './components/data'
export default {
  name: 'App',
  data() {
    return{
      count: 0,
      text: []
    }
  },
  
  methods: {
    handleSubmit () {
      console.log('The form has been submitted')

      let amount = parseInt(this.count)

      if (amount > 8){
        amount = 8
      }

      if (amount < 0){
        amount = 1
      }

      this.text = data.slice(0, amount)
    }
  },

}
</script>

<style src="./assets/index.css" ></style>
