<template>
    <!-- <div class="section-center" :v-for="menu in menu">
        <article class="menu-item">
            <img :src="menu.img" :alt='menu.title'/>
            <header>
                <h4>{{menu.title}}</h4>
                <h4 class="price">{{menu.price }} </h4>
            </header>
            <p class="item-text">{{menu.desc}} </p>
        </article>
    </div> -->
    <div class="section-center">
        <article class="menu-item">
            <img class="photo" alt='item' />
            <header>
                <h4>Menu Item One</h4>
                <h4 class="price">#120,000</h4>
            </header>
            <p class="item-text">this is the description of the process and all that is involved.</p>
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
       
    }

}
</script>

<style src='../assets/index.css'>

</style>