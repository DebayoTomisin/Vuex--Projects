<template>
    <article class="review">
        <div class="img-container">
            <img :src="info.image" :alt="info.name" class="person-img"/>
        </div>
        <h4 class="author">{{info.name}}</h4>
        <p class="job">{{info.job}}</p>
        <p class="info">{{info.text}}</p>

        <div class="button-container">
            <button class="prev-btn" @click="prevPerson">Previous Btn</button>
            <button class="next-btn" @click="nextPerson">Next Button</button>
            <button class="random-btn" @click="randomPerson">surprise me</button>
        </div>
    </article>
</template>

<script>
    import reviewData from './data'

    export default {
        name: 'Reviews',
        data () {
            return{
                data: [],
                index: 0,
                name: '',
                job: '',
                image: '',
                text: '',
                info: {}
            }
        },
        created () {
            this.data = reviewData
            const {name, job, image, text} = this.data[this.index]
            
            this.info = {
                name: name,
                job: job,
                image: image,
                info: text,
            }
        },
        methods: {
            checkNumbers (number) {
                if (number < 0){
                    return this.data.length
                }
                if (number > this.data.length - 1){
                    return 0
                }
                return number
            },

            randomPerson () {
                let randomNumber = Math.floor(Math.random() * this.data.length)
                if (randomNumber === this.index) {
                    randomNumber += 1
                }
                this.index = this.checkNumbers(randomNumber)
                console.log(this.index)
            },

            prevPerson () {
                this.index = () => {
                    let newIndex = this.index + 1
                    return this.checkNumbers(newIndex)
                }
            },

            nextPerson () {
                this.index= () => {
                    let newIndex = this.index - 1
                    return this.checkNumbers(newIndex)
                }
            },

        }
    }

</script>

<style src='../assets/index.css' scoped>

</style>