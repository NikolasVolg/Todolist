<template>
  <div id="app">

  
    <todos></todos>
    
  </div>
</template>

<script>
import Todos from './components/Todos'

export default {

  name: 'App',

  data: () => {

    return {
      todos: [{
        name: 'Demo',
        completed: true
      }]
    }
  },

  components: {
    Todos
  }
}
</script>

