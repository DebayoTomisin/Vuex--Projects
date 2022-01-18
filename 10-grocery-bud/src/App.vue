<template>
  <section class="section-center">
    <form @submit.prevent="handleSubmit" class="grocery-form">
      <h3>Grocery Bud</h3>
      <div class="form-control">
        <input type="text" placeholder="Enter a Value" v-model="name" class="grocery">
        <button class="submit-btn" type="submit" >{{isEditting ? 'edit' : 'submit'}}</button>
      </div>
    </form>
  </section>
</template>

<script>
export default {
  name: 'App',
  components: {
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
    },

    removeItem (id) {
      this.showAlert(true, 'Item has been removed', 'danger')
      this.list = this.list.filter(item => item.id !== id)
    },

    handleSubmit () {
      console.log("Allow me to enjoy myself")

      if (!this.name){
        this.showAlert(true, 'Enter a grocery item', 'danger')
      }
      else if (this.name && this.isEditting) {
        let list = this.list.map((item) => {
          if(item.id === this.editId){
            return {...item, title: this.name}
          }
          this.list = list
        })
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
    
  },
  created () {
    this.list = this.getLocalStorage()
  },
  // updated() {
  //   console.log(this.list)
  // }
}
</script>

<style src="./assets/index.css"></style>
