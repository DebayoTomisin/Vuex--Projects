<template>
    <div class="grocery-list" v-for="(item, index) in listItem" :key="index">
        <article>
            <p class="title">{{item.title}}</p>
            <div class="btn-container">
                <button class="btn edit-btn" type="button" @click='$emit("edit-item", item.id)' >
                    <img src="../assets/editing.png" alt="edit" class="icons" />
                </button>
                <button class="btn delete-btn" type="button" @click='$emit("remove-item", item.id)' >
                    <img src="../assets/delete.png" alt="delete" class="icons" />
                </button>
            </div>
        </article>
    </div>
</template>

<script>
export default {
    name:'List',
    data(){
        return{
            listItem: Array
        }
    },
    props: {
        items: Array
    },
    emits: ['edit-item', "remove-item"],
    // methods: {
    //     editItem(id) {
    //         this.$emit("edit-item", id)
    //     },
    //     removeItem(id) {
    //         this.$emit("remove-item", id)
    //     }
    // },
    computed: {
    },
    beforeUpdate() {
        this.listItem = this.items
    },
    created() {
        this.listItem = this.items
    }
    
}
</script>

<style lang="css" scoped>
article{
    margin: 12px 0;
    display: flex;
    justify-content: space-between;
}
.icons{
    height:20px;
    width: 20px;
    display: flex;
}
</style>