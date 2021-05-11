<template>
  <div>
    <input type="text" v-model.lazy="newItem" placeholder="Add an Item">
    {{newItem}}
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
      items:[
        {id:1, label:'banana'},
        {id:2, label:'apple'},
        {id:3, label:'tea'},
      ]
    }
  },
}
</script>
