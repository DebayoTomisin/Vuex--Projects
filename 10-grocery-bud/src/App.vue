<template>
  <section class="section-center">
    <Alert v-show="alert.show" :list="list" :type="alert.type" :msg="alert.msg" v-on:remove-alert="showAlert" />
    <form @submit.prevent="handleSubmit" class="grocery-form">
      <h3>Grocery Bud</h3>
      <div class="form-control">
        <input type="text" placeholder="Enter a Value" v-model="name" class="grocery">
        <button class="submit-btn" type="submit" >{{isEditting ? 'edit' : 'submit'}}</button>
      </div>
    </form>

    <div v-show="list.length > 0" class="grocery-containe">
      <List :items="list" v-on:edit-item="editList" v-on:remove-item="removeItem" />
      <button @click="clearList" class="clear-btn">clear items</button>
    </div>
  </section>
</template>

<script>
import Alert from "./components/Alert.vue"
import List from './components/List.vue'
export default {
  name: 'App',
  components: {
    Alert,
    List
  },
  data() {
    return {
      name: '',
      isEditting: false,
      list: [],
      alert: {
        show: false,
        msg: '',
        type: '',
      },
      editId: null
    }
  },
  methods: {
    getLocalStorage () {
      let list  = localStorage.getItem('list')
      if (list) {
        return JSON.parse(localStorage.getItem('list'))
      } else {
        return []
      }
    },
    
    showAlert(show=false, msg='', type="") {
      this.alert = {
        show: show,
        msg: msg,
        type: type
      }
    },

    clearList () {
      this.showAlert(true, 'List has been cleared', 'success')
      this.list = []
    },

    editList (id) {
      const specItem = this.list.find(item => item.id === id)
      this.isEditting = true
      this.editId = id
      this.name = specItem.title
      console.log(this.editId)
    },

    removeItem (id) {
      this.showAlert(true, 'Item has been removed', 'danger')
      this.list = this.list.filter(item => item.id !== id)
    },

    handleSubmit () {
      if (!this.name){
        this.showAlert(true, 'Enter a grocery item', 'danger')
      }
      else if (this.name && this.isEditting) {
        let list = this.list.map((item) => {
          if(item.id === this.editId){
            return {...item, title: this.name}
          }
        })
        this.list = list
        this.name = ""
        this.editId = null
        this.isEditting = false
        this.showAlert(true, 'Value has changed', 'success')
      }
      else {
        const newItem = { id: new Date().getTime().toString(), title: this.name}
        this.list = [...this.list, newItem]
        this.name = ""
      }
    }
  },
  computed: {
    // setLocalStorage () {
    //   return localStorage.setItem('list',JSON.stringify(this.list))
    // },
  },
  created () {
    this.list = this.getLocalStorage()
  },

  beforeUpdate() {
    localStorage.setItem('list',JSON.stringify(this.list))
    this.list = this.getLocalStorage()
    //console.log(this.list)
  },
}
</script>

<style src="./assets/index.css"></style>
