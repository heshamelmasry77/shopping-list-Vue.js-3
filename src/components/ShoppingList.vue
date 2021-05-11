<template>
  <div>
    <input type="text" v-model="newItem" placeholder="Add an Item">
    <label>
      <input type="checkbox" v-model="newItemHighPriority">
      <strong>High Priority</strong>
    </label>
    <br/>
    {{newItem}} || {{newItemHighPriority}}
    <br/>
    <label><input type="checkbox" v-model="iceCreamFlavours" value="vanilla">vanilla</label>
    <label><input type="checkbox" v-model="iceCreamFlavours" value="chocolate">chocolate</label>
    <label><input type="checkbox" v-model="iceCreamFlavours" value="strawberry">strawberry</label>
    <label><input type="checkbox" v-model="iceCreamFlavours" value="mango">mango</label>
    <ul>
      <li v-for="item in items" :key="item.id">{{item.label}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newItem:'',
      newItemHighPriority: false,
      iceCreamFlavours:[],
      items:[
        {id:1, label:'banana'},
        {id:2, label:'apple'},
        {id:3, label:'tea'},
      ]
    }
  },
}
</script>
