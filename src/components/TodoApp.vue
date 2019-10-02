<template>
    <div id='todo-app'>
        
        <div id='title'>
            Todo List
        </div>
        <TodoAdd 
            v-bind:id="id" 
            v-bind:title="title"
            v-on:onChange="onChange"
            v-on:addTodo='addTodo'
        />
        <TodoList 
            v-bind:todos="todoList"
            v-on:delTodo="delTodo"
            v-on:toggle="toggle"
        />
    </div>
</template>

<script>


import TodoAdd from './TodoAdd.vue'
import TodoList from './TodoList.vue'

export default {
  name: 'TodoApp',
  data(){
      return {
        id: 3,
        title: '',
        todoList: [
            {id: 0, text: 'Java', done: true},
            {id: 1, text: 'javaScript', done: false},
            {id: 2, text: 'SQL', done: false},
        ],
        
      }
  },
  methods: {
      onChange(title) {
          this.title = title;
      },
      addTodo(title) {
          const todo = {
              id: this.id++,
              text: title,
              done: false
          }
          this.todoList.push(todo);
          this.title = '';
      },
      delTodo(index) {
          this.todoList.splice(index, 1)
      },
      toggle(index, checked) {
          this.todoList[index].done = !checked
      }
  },
    
  components: {
      TodoAdd,
      TodoList
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

#todo-app {
    width: 50%;
    
    background-color: rgb(230, 230, 230);
    border-radius: 10px;

    padding: 1rem;
    text-align: center;
}

#title {
    font-size: 2rem;
    padding: 1rem;
}
</style>
