<template>
    <article class="review">
        <div class="img-container">
            <img :src={image} :alt="name"/>
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
                index: 0
            }
        },
        created () {
            this.data = reviewData
            const {name, job, image, text} = this.data[this.index]
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