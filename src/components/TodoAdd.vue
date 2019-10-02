<template>
    <div id='todo-add'>
        <div id='label'>Title</div>
        <input type='text' 
            v-model="title" 
            v-on:keyup="onChange(title)"
            v-on:keyup.enter="addTodo(title)"
        />
        <button id='add' 
            v-on:click="addTodo(title)"
            
        >Add</button>
    </div>
</template>

<script>
export default {
  name: 'TodoAdd',
  props: ['id', 'title'],
  methods: {
      onChange(title) {
          this.$emit('onChange', title);
      },
      addTodo(title) {
          if ( title === '' ) {
              return;
          }
          this.$emit('addTodo', title);
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

#todo-add {
    height: 1.4rem;
    width: 90%;
    display: flex;
    border-radius: 5px;
    background-color: white;
    padding: 5%
}

#label {
    width: 20%;
}

input {
    margin-left: 10px;
    margin-right: 10px;
    width: 80%;
}

#add {
    width: 20%;
}



</style>
