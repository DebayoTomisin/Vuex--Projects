<template>
    <div class="grocery-list" v-for="(index, item) in items" :key="index">
        <article>
            <p class="title">{{item.id}}</p>
            <div class="btn-container">
                <button class="edit-btn" type="button">
                    <img src="../assets/editing.png" alt="edit" class="icons" />
                </button>
                <button class="delete-btn" type="button">
                    <img src="../assets/delete.png" alt="delete" class="icons" />
                </button>
            </div>
        </article>
    </div>
</template>

<script>
export default {
    name:'List',
    props: {
        items: Array
    },
    mounted() {
        console.log(this.items)
    }
}
</script>

<style lang="css" scoped>
.icons{
    height:20px;
    width: 20px
}
</style>