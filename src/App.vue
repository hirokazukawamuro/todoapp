<script>
export default {
  data() {
    return {
      input:{
        text:'',
        isDone: false,
      },
      todos:[],
    }
  },
  methods: {
    addList() {
      if(this.input.text === ''){
        alert('文字を入力してください')
        return
      }
      else{
        this.todos.push(this.input)
        this.input = {
          text:'',
          isDone: false,
        }
      } 
    },

    clearDoneTodos(){
      this.todos = this.todos.filter((todo) => !todo.isDone)
    },
  },
}

</script>

<template>
  <h1>My ToDo App</h1>
  <input type="text" v-model="input.text"/>
  <button @click="addList">追加</button><button @click="clearDoneTodos">完了済みを削除する</button>
  <p v-if="todos.length === 0">ToDoがまだありません！</p>
  <ul v-else>
    <li v-for="todo in todos">
    <input type="checkbox" v-model="todo.isDone"/><span :class="{ 'todo-done' : todo.isDone}">{{ todo.text }}</span></li>
  </ul>
</template>

<style>
body {
  background-color: #eee;
}

.todo-done {
  text-decoration: line-through;
}

ul{
  list-style: none;
}

li{
  text-align: left;
}
</style>