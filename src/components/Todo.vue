<template>
  <div class='todoCard'>
    <h1>Todo List</h1>
    <div class="items" v-bind:key='todo.id' v-for='todo in todos'>
      <TodoItem v-bind:todo='todo' v-on:del-todo='deleteTodo'/>
    </div>
    <div class="addItem"  >
      <AddItem v-on:add-todo="addTodo"/>
    </div>

  </div>
</template>

<script>
import TodoItem from './TodoItem'
import AddItem from './AddItem'
export default {
  name: 'Todo',
  components: {
    TodoItem,
    AddItem
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(element => element.id !== id)
    },
    addTodo(newTodo){
      newTodo.id = this.currId
      this.todos.push(newTodo)
      this.currId++
    }
  },
  data() {
    return {
      todos: [],
      currId: 1
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h1{
    margin: 0;
    background: whitesmoke;
    color: #4776a5;
  }
  .todoCard{
    padding: 25px;
    box-shadow: 2px 3px 8px lightgrey;
    margin-bottom: 400px;
  }


</style>
