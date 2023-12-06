<template>
  <div class="content">
  <h1>ToDo App</h1>
  <p><span style="color: darkslategray;">Features: </span>Ability to Create, Edit and Delete a Todo</p> 
  <div class="body">
    <input v-model="newItem" placeholder="Add a new task"  @keyup.enter="addItem" >
  <button @click="addItem">Add</button>
  <ul>
    <li v-for="(item, index) in items" :key="index">
      {{item}} 
      <br />
      <button class="btnedt" @click="editItem(index)">Edit</button>
      <button class="btndel" @click="deleteItem(index)">Delete</button>
    </li>
  </ul>
  </div>
  
</div>
</template>

<script>
  export default {
  data() {
  return {
    newItem: '',
    items: []
  }
},
  methods: {
    addItem() {
      this.items.push(this.newItem);
      this.newItem = '';
    },
    deleteItem(index) {
      this.items.splice(index, 1);
    },
    editItem(index) {
      const newItem = prompt('Update Todo:', this.items[index]);
      if(newItem !== null){
        this.items[index] = newItem;
      }
    }
  }
  }
</script>

<style scoped>
.content{
  margin-top: 100px;
}

h1, p, .body {
  text-align: center;
}

h1{
  color: darkslategray;
}

li{
  list-style-type: none;
  padding: 5px;
  margin-bottom: 5px;
}

ul{
  margin-right: 75px;
}

button{
  background-color: darkslategray;
  color: white;
  margin-left: 5px;
  margin-right: 5px;
  border-radius: 15px;
  padding-left: 10px;
  padding-right: 10px;
}

.btndel:hover{
  background-color: red;
}

.btnedt:hover{
  background-color: darkcyan;
}
</style>