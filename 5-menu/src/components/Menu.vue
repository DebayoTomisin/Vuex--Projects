<template>
    <div class="section-center" v-for="(menu, idx) in menu" :key='idx'>
        <article class="menu-item">
            <img :src="menu.img" :alt='menu.title'/>
            <header>
                <h4>{{menu.title}}</h4>
                <h4 class="price">{{menu.price }} </h4>
            </header>
            <p class="item-text">{{menu.desc}} </p>
        </article>
    </div>
</template>

<script>
export default {
    name: 'Menulist',
    props: {
        menu: Array
    },
    created() {
       console.log(this.menu)
    }

}
</script>

<style src='../assets/index.css' scoped>

</style>