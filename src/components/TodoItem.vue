<template>
  <div class="item" >
    <div class='item-container'>
      <input class='checkbox' type="checkbox" v-on:click="toggleComplete" v-bind:checked="todo.complete">
      <p v-bind:class="{'is-complete':todo.complete}">{{todo.title}}</p>
      <button class="button" @click="$emit('del-todo', todo.id)">
        <p>X</p>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  methods: {
    toggleComplete() {
      this.todo.complete = !this.todo.complete;
    }
  }
};
</script>

<style scoped>
.is-complete {
  text-decoration: line-through;
  margin: 0;
}
.button {
  border: none;
  height: 16px;
  background: rgb(228, 119, 119);
  border-radius: 18px;
  color: whitesmoke;
  font-weight: 900px;
}
.button p {
  margin: 0px;
  display: flex;
}
.item{
  box-shadow: 1px 1px 5px lightgrey;
  background: white;
}
.item-container{
    margin: 8px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 25px;
}
</style>
