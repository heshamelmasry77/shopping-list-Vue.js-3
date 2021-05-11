<template>
  <div>
    <div class="header">
      <h1>Shopping List App</h1>
      <button v-if="editing" v-on:click="doEdit(false)" class="btn btn-cancel">Cancel</button>
      <button v-else v-on:click="doEdit(true)" class="btn btn-primary">Add Item</button>
    </div>
    <div v-if="editing" class="add-item-form">
      <input v-on:keyup.enter="saveItem" type="text" v-model="newItem"
             placeholder="Add an Item">
      <label>
        <input
            type="checkbox" v-model="newItemHighPriority">
        <strong>High Priority</strong>
      </label>
      <div>
        <button v-on:click="saveItem" class="btn btn-primary">Save Item</button>
      </div>
    </div>
    <p v-if="items.length === 0">Nice Job!, You have bought all your items</p>
    <ul>
      <li v-for="item in items" :key="item.id">{{ item.label }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      editing: false,
      newItem: '',
      newItemHighPriority: false,
      iceCreamFlavours: [],
      items: [
        {id: 1,label: 'banana'},
        {id: 2,label: 'apple'},
        {id: 3,label: 'tea'},
      ]
    }
  },
  methods: {
    saveItem() {
      this.items.push({id: this.items.length + 1,label: this.newItem})
      this.newItem = "" // reset newItem
    },
    doEdit(editing) {
      this.editing = editing
      this.newItem = ""
    }
  }
}
</script>
