<template>
  <div id="app">
    <h1>To Do List</h1>
    <input type="text" v-model="userInput" @keydown.enter="addToList()">
    <button @click="addToList()">Add</button>
    <hr>
    <ul>
      <li v-for="(item, index) in toDoList" :key="index">
        <input type="checkbox" @click="toggleCompleted(index)">
        <span :class="item.completed ? 'done' : ''">{{ item.name }}</span>
        <button @click="removeItem(index)">X</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      userInput: '',
      toDoList: []
    }
  },
  methods: {
    addToList () {
      if (this.userInput === '') return
      this.toDoList.push({
        name: this.userInput,
        completed: false
      })
      this.userInput = ''
    },
    toggleCompleted (index) {
      this.toDoList[index].completed = !this.toDoList[index].completed
    },
    removeItem (index) {
      this.toDoList.splice(index, 1)
    }
  }
}
</script>

<style>
  .done {
    text-decoration: line-through;
  }
</style>
