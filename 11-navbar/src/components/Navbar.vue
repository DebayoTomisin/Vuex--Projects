<template>
    <nav>
        <div class="nav-center">
            <div class="nav-header">
                <img src="../assets/logo.svg" alt='logo' />
                <button class="nav-toggle" @click="toggleLinks">
                    <img src='../assets/bars-svgrepo-com.svg' alt='bars' />
                </button>
            </div>
            <div class="links-container">
                <ul class="links" v-for="link in links" :key="link.id">
                    <li>
                        <router-link :to="link.url">{{link.text}}</router-link>
                    </li>
                </ul>
            </div>
            <div class="social-icons" v-for="icon in social" :key="icon.id">
                <li>
                    <a :href="icon.url"><img :src="icon.icon" /></a>
                </li>
            </div>
        </div>
    </nav>
</template>

<script>
import { links, social } from './data'
export default {
    name: 'Navbar',
    data (){
        return {
            showLinks: false,
            links: links,
            social: social
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