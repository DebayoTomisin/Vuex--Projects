<template>
    <article class="review">

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
            }

        }
    }

</script>

<style src='../assets/index.css' scoped>

</style>