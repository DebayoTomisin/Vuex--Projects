<template>
  <main class="menu section">
    <div class="title">
      <h2>Our Menu</h2>
    </div>
    <div class="underline"></div>
    <Categories :categories="categories" :filter-cat="filterCat" />
    <MenuList :menu="menu" />
  </main>
</template>

<script>
import Menu from './components/data'
import Categories from './components/Categories'
import MenuList from './components/Menu'

export default {
  name: 'App',
  components: {
    Categories,
    MenuList,
  },
  data(){
    return{
      menu : Menu,
      categories: []
    }
  },
  mounted () {
    this.categories = ['all', ...new Set(Menu.map(item => item.category))]
  },
  methods: {
    filterCat (category) {
      if (category == 'all'){
        this.menu = Menu
        return
      }
      const newCat = Menu.filter(item => item.category === category)
      this.menu = newCat
    }
  }
}
</script>

<style src="./assets/index.css">

</style>