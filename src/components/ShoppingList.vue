<template>
  <div>
    <input v-on:keyup.enter="items.push({id: items.length + 1, label:newItem})" type="text" v-model="newItem"
           placeholder="Add an Item">
    <label>
      <input
          type="checkbox" v-model="newItemHighPriority">
      <strong>High Priority</strong>
    </label>
    <div>
      <button v-on:click="items.push({id: items.length + 1, label:newItem})" class="btn btn-primary">Save Item</button>
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
}
</script>
