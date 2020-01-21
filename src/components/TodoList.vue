<template>
  <div>
    <b-card header="TodoList" header-tag="header">

      <b-list-group>
        <TodoItem v-for="item in list" :todo="item" :key="item.id" v-on:complete-todo="completeTodo" v-on:delete-todo="deleteTodo"/>
      </b-list-group>

      <template v-slot:footer>
        <input type="text" v-model="newTodo" v-on:keyup.enter="addNewTodo()" />
        <b-button class="float-right" variant="primary" @click="addNewTodo()">Add</b-button>
      </template>
    </b-card>
  </div>
</template>

<script>
/* eslint-disable no-console */
import TodoItem from './TodoItem';
export default {
  name: "TodoList",
  components: {
    TodoItem,
  },
  data() {
    return {
      list: [{
          id: 1,
          text: "Clean the house",
          done: true
        },
        {
          id: 2,
          text: "Buy bread",
          done: false
        },
        {
          id: 3,
          text: "Create todo app",
          done: false
        }

      ],
      newTodo: ""
    };
  },
  methods: {
    addNewTodo() {
      if (!this.newTodo) {
        alert("please enter todo text");
        return;
      }
      const newId = Math.max.apply(null, this.list.map(t => t.id)) + 1;
      this.list.push({
        id: newId,
        text: this.newTodo,
        done: false
      });
      this.newTodo = "";
    },
    completeTodo(todo) {

      console.log(todo);
      const todoIndex = this.list.indexOf(todo);

      this.list[todoIndex].done = true;
    },
    deleteTodo(todo) {
    const todoIndex = this.list.indexOf(todo);

    this.list.splice(todoIndex,1);
    }
  }
};
</script>

<style>
</style>
