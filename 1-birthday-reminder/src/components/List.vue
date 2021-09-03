<template>
    <article :key="person.id"  v-for="person in people" class="person">
        <img :src="person.image" alt="person image" />
        <div>
            <h4>{{person.name}} </h4>
            <p>{{person.age}} years</p>
        </div>
    </article>
</template>

<script>
    export default {
        name: 'Lists',
        props: {
            people: Array
        }
    }
    
</script>

<style src="../assets/index.css">

</style>