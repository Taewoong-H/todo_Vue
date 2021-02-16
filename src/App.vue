<template>
  <div>
    <TodoHeader />
    <TodoTitle />
    <TodoInput v-on:addItem="addOneItem" />
    <TodoController />
    <TodoList v-bind:props="toDoItems" />
    <TodoFooter />
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader';
import TodoTitle from './components/TodoTitle';
import TodoInput from './components/TodoInput';
import TodoController from './components/TodoController';
import TodoList from './components/TodoList';
import TodoFooter from './components/TodoFooter';

import getDate from './utils/getDate.js';

export default {
  name: 'App',
  data() {
    return {
      toDoItems: []
    };
  },

  methods:{
    addOneItem(toDoItem){
      const toDoData = {
        item: toDoItem,
        data: `${getDate().date}/${getDate().week}`,
        time: getDate().time,
        completed: false
      };

      localStorage.setItem(toDoItem, JSON.stringify(toDoData));
      this.toDoItems.push(toDoData);
    }
  },

  created() {
    if (localStorage) {
      for (let i = 0; i < localStorage.length; i++) {
        if (localStorage.key(i) !== "loglevel:webpack-dev-server") {
          this.toDoItems.push(JSON.parse(localStorage.getItem(localStorage.key(i))));
        }
      }
    }
  },

  components: {
    TodoHeader,
    TodoTitle,
    TodoInput,
    TodoController,
    TodoList,
    TodoFooter
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
