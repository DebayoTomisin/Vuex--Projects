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
                value: 0
            }
        },
        props: ['people', 'index'],
        updated() {
            this.value = this.index
        }
    }
</script>

<style>

</style>