<script>
export default {
  data() {
    return {
      input:{
        text:'',
        checked: true,
      },
      todos:[],
    }
  },
  methods: {
    addList() {
      this.todos.push(this.input)
      this.input = {
        text:'',
        checked: true,
      }
    }
  },
}

</script>

<template>
  <h1>My ToDo App</h1>
  <input type="text" v-model="input.text"/>
  <button @click="addList">追加</button><button>完了済みを削除する</button>
  <p v-if="todos.length === 0">ToDoがまだありません！</p>
  <ul v-else>
    <li v-for="todo in todos">
    <p>{{ todo.text }}<input type="checkbox"></p></li>
  </ul>
</template>

<style>
body {
  background-color: #eee;
}

.todo-done {
  text-decoration: line-through;
}
</style>