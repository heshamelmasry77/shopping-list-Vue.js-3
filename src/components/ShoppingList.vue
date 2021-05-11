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
        <button v-bind:disabled="newItem.length === 0" v-on:click="saveItem" class="btn btn-primary">Save Item</button>
      </div>
    </div>
    <p v-if="items.length === 0">Nice Job!, You have bought all your items</p>
    <ul>
      <li @click="togglePurchased(item)"
          :class="[item.purchased ? 'strikeout' : 'underline' , item.highPriority ? 'priority' : '']"
          v-for="item in reversedItems" :key="item.id">{{ item.label }}
      </li>
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
        {id: 1,label: 'banana',purchased: true,highPriority: true},
        {id: 2,label: 'apple',purchased: false,highPriority: true},
        {id: 3,label: 'tea',purchased: false,highPriority: true},
      ]
    }
  },
  computed:{
    reversedItems(){
      return [...this.items].reverse()
    }
  },
  methods: {
    saveItem() {
      this.items.push({
        id: this.items.length + 1,
        label: this.newItem,
        highPriority: this.newItemHighPriority
      })
      this.newItem = "" // reset newItem
      this.newItemHighPriority = false
    },
    doEdit(editing) {
      this.editing = editing
      this.newItem = ""
      this.newItemHighPriority = false
    },
    togglePurchased(item) {
      item.purchased = !item.purchased;
    }
  }
}
</script>
