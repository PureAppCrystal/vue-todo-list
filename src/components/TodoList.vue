<template>
    <div id='todo-list'>
        <div id='todo' v-for="(todo, index) in todos" :key='todo.id'>
            <input type='checkbox' 
                v-model="todo.done"
            />
            <del v-if="todo.done" v-on:click="toggle(index, todo.done)" >
                <!-- <span v-on:click="toggle(index, todo.done)">{{index+1}} {{todo.text}}</span> -->
                {{index+1}} {{todo.text}}
                <button v-on:click="delTodo(index)">Delete</button>
            </del>
            <template v-else>
                <span v-on:click="toggle(index, todo.done)"> {{index+1}} {{todo.text}} </span>
                <button v-on:click="delTodo(index)">Delete</button>
            </template>
            
        </div>
    </div>
</template>

<script>
export default {
  name: 'TodoList',
  props: ['todos'],
  methods: {
      toggle(index, checked) {
          this.$emit('toggle', index, checked)
      },
      delTodo(index) {
          this.$emit('delTodo', index);
      }
  }
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

#todo-list {
    margin-top: 1rem;
    width: 90%;
    flex: 1;
    padding: 5%;

    background-color: white;
    border-radius: 5px;
    text-align: left;
}

#todo {
    height:1.4rem;
}

#todo + #todo {
    margin-top: 10px;
}


button {
    height: 100%;
    width: 20%;
    float: right;
}

</style>
