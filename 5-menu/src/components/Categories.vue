<template>
    <div class='btn-container' v-for="(cat, idx) in categories"  :key="idx">
        <button class="filter-btn" type="button" @click="flterCats(cat)">
           {{ cat }}
        </button>
    </div>

</template>

<script>
export default {
   name: 'Categories',
   props: {
       categories: Array,
       filterCat: Function,
   },
   created() {
       
   },
   emit : ['filterCat']
}

</script>

<style src='../assets/index.css' scoped>

</style>