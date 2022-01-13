<template>
    <article v-for="(person, personIndex) in people" :key="personIndex" :class="position">
        <img src="{{person.image}}" alt="image" class="person-img" />
        <h4>{{ person.name }}</h4>
        <p className="title">{{person.title}}</p>
        <p className="text">{{person.quote}}</p>
    </article>
</template>

<script>
    export default {
        name: 'People',
        data(){
            return{
                position: 'activeSlide'
            }
        },
        props: ["people", "index"],
        computed: {},
        methods: {
            getValue(){
                let position = 'nextSlide'
                this.people.map((person, personIndex) => {
                    if(personIndex == this.index){
                        position = "activeSlide"
                    }
                    
                    if(personIndex === this.index - 1 || (this.index == 0 && personIndex === this.people.length - 1)) {
                        position= "lastSlide"
                    }
                })
                return position
            }
            
        },
        updated () {
            this.position = this.getValue()
        },
    }
</script>

<style>

</style>