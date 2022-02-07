<template>
    <nav>
        <div class="nav-center">
            <div class="nav-header">
                <img src="../assets/logo.svg" alt='logo' />
                <button class="nav-toggle" @click="toggleLinks()">
                    <img src='../assets/bars-svgrepo-com.svg' />
                </button>
            </div>
        </div>
    </nav>
</template>

<script>

export default {
    name: 'Navbar',
    data (){
        return {
            showLinks: false
        }
    },
    methods: {
        toggleLinks () {
            this.showLinks = !this.showLinks
            console.log(this.showLinks)
        }
    },
    updated () {},
}
</script>

<style>

</style>