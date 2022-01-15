<template>
    <article :class="position">
        <img :src="(`${people[value].image}`)" alt="image" class="person-img" />
        <h4>{{ people[value].name }}</h4>
        <p className="title">{{people[value].title}}</p>
        <p className="text">{{people[value].quote}}</p>
    </article>
</template>

<script>
    export default {
        name: 'People',
        data(){
            return{
                position: 'activeSlide',
                value: this.index
            }
        },
        props: ['people', 'index'],
        computed: {},
    }
</script>

<style>

</style>