<template>
  <div>
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
    <ul>
      <li v-for="item in items" :key="item.id">{{ item.label }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
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
  methods:{
    saveItem(){
      this.items.push({id: this.items.length + 1, label:this.newItem})
      this.newItem = "" // reset newItem
    }
  }
}
</script>
