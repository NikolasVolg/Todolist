<template>
  <div id="app">
  <carrousel>

    <carrousel-slide v-for="n in slides" :key="n.id" :index="n-1">
      <!-- <div>Slide {{ n }}</div> -->
      <img :src="'https://picsum.photos/1000/50' + n" style="width: 100%">
    </carrousel-slide>

  </carrousel>

  <button @click="addSlide">Ajouter un slide</button>
  <button @click="removeSlide">supprimer un slide</button>
  
    <todos></todos>
    
  </div>
</template>

<script>
import Todos from './components/Todos'
import carrousel from './components/carrousel/carrousel'
import carrouselSlide from './components/carrousel/carrouselSlide'

export default {

  name: 'App',

  data: () => {

    return {

      slides: 5,

      todos: [{
        name: 'Demo',
        completed: true
      }]
    }
  },

  methods: {
    addSlide () {
      this.slides++
    },

    removeSlide () {
      this.slides--
    }
  },

  components: {

    Todos,
    carrousel,
    carrouselSlide
  }
}
</script>

