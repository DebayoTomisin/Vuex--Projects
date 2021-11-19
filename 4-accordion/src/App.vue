<template>
  <main>
    <div class='container'>
      <h3>Questions and Answers about container</h3>
      <section class='info' v-for='question in data' :key='question.id'>
        <Question :question="question" @toggleInfo='toggleInfo' :showInfo="showInfo"  />
      </section>
    </div>
  </main>
</template>

<script>
import Question from './components/Question.vue'
import questions from './components/data.js'

export default {
  name: 'App',
  components: {
    Question
  },
  data () {
    return {
      data : [],
      showInfo: false
    }
  },

  methods: {
    toggleInfo() {
      this.showInfo = !this.showInfo
    }
  },

  created(){
    this.data = questions
  }
}
</script>

<style src='./assets/index.css' scoped>

</style>
