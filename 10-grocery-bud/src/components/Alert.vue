<template>
    <p :class="`alert alert-${this.type}`">{{msg}}</p>
</template>

<script>
export default {
    name: 'Alert',
    props: {
        list: Array,
        msg: String,
        type: String
    },
    methods: {
        removeAlert() {
            this.$$emit("remove-alert")
        }
    },
    watch: {
        'this.list' : {
            handler() {
                const timeout = setTimeout(() => this.removeAlert(), 3000)
                return () => clearTimeout(timeout)
            }
        }
    },
}
</script>

<style>

</style>