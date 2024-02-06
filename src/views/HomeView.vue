<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <h1>desde Home</h1>
    <div class="content">
      <div v-for="character in characters" :key="character.id">
        <img :src="character.image" alt="">
        <div>{{character.name}}</div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios'

export default {
  name: 'HomeView',
  components: {
  },
  data(){
    return {
      characters: []
    }
  },
  mounted(){
    console.log('verificando')
    this.getTodos();
  },
  methods: {
    getTodos(){
      axios.get('https://rickandmortyapi.com/api/character')
      .then(res => {
        this.characters = res.data.results
      })
      .catch(e => {
        console.log(e)
      })
    }
  }
}
</script>

<style scoped>
body{
  background: black;
}
.content{
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
  grid-template-rows: 1fr;
  gap: 0px 10px;
}
</style>
