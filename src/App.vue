<template>
  <div>
    <TodoHeader />
    <TodoTitle v-bind:props="checkCount" />
    <TodoInput v-on:addItem="addOneItem" />
    <TodoController v-on:sortItem="sortAllItem" v-on:clearAll="clearAllItem"/>
    <TodoList v-bind:props="toDoItems" v-on:removeItem="removeOneItem" v-on:toggleItem="toggleOneItem" />
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
  components: {
    TodoHeader,
    TodoTitle,
    TodoInput,
    TodoController,
    TodoList,
    TodoFooter
  },

  data() {
    return {
      toDoItems: []
    };
  },

  methods:{
    addOneItem(toDoItem){
      const toDoData = {
        item: toDoItem,
        date: `${getDate().date}/${getDate().week}`,
        time: getDate().time,
        completed: false
      };

      localStorage.setItem(toDoItem, JSON.stringify(toDoData));
      this.toDoItems.push(toDoData);
    },

    removeOneItem(toDoItem, index) {
      localStorage.removeItem(toDoItem.item);
      this.toDoItems.splice(index, 1);
    },

    toggleOneItem(toDoItem) {
      toDoItem.completed = !toDoItem.completed;
      localStorage.setItem(toDoItem.item, JSON.stringify(toDoItem));
    },

    clearAllItem() {
      this.toDoItems = [];
      localStorage.clear();
    },

    sortTodoLatest() {
      this.toDoItems.sort((a, b) => {
        return b.time - a.time;
      })
    },

    sortTodoOldest() {
      this.toDoItems.sort((a, b) => {
        return a.time - b.time
      })
    },

    sortAllItem(selectedSort) {
      if (selectedSort.value === "date-desc") {
        this.sortTodoLatest();
      } else if (selectedSort.value === "date-asc") {
        this.sortTodoOldest();
      }
    }
  },

  computed: {
    checkCount() {
      const checkLeftItems = () => {
        let leftCount = 0;
        this.toDoItems.forEach((item) => {
          if (item.completed === false) {
            leftCount++;
          }
        })
        return leftCount;
      };

      const count = {
        total: this.toDoItems.length,
        left: checkLeftItems()
      };
      
      return count
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
