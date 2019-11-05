<template>
  <main id="app">
    <List :items='pokemons' />
  </main>
</template>

<script>
import axios from 'axios'
import List from './components/List.vue'

function _parseData(list) {
  let pokemons = [];

  for (let pokemon of list) {
    axios.get(pokemon.url)
      .then(res => {
        pokemons.push({
          name: ((res || {}).data || {}).name || '',
          url: (((res || {}).data || {}).sprites || {}).front_default || ''
        })
    })
  }
  
  this.pokemons = pokemons
}


export default {
  name: 'app',
  data: () => ({
    pokemons: []
  }),
  components: {
    List
  },
  methods: {
    _parseData
  },
  mounted() {
    axios.get('https://pokeapi.co/api/v2/pokemon/')
      .then(res => {
        const list = ((res || {}).data || {}).results || []
        this._parseData(list)
      })
  }
}
</script>