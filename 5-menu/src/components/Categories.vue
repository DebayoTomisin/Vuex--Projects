<template>
    <div class="btn-container" :v-for="cat in categories">
        <button class="filter-btn" type='button'>
            {{ cat }}
        </button>
    </div>

</template>

<script>
export default {
   name: 'Categories',
   props: {
       categories: Array
   },
   created() {
       console.log(this.categories)
   }
}

</script>

<style src='../assets/index.css' scoped>

</style>