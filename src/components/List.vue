<template>
  <section>
    <article v-for='(pokemon, key, index) in items' :key='index'>
      <ItemList :url='pokemon.url' :name='pokemon.name' :background='_generateBackgroundColor()'></ItemList>
    </article>
  </section>
</template>

<script>
import axios from 'axios'
import ItemList from './ItemList.vue'

function _generateBackgroundColor() {
  const red = Math.floor(Math.random() * 256)
  const green = Math.floor(Math.random() * 256)
  const blue = Math.floor(Math.random() * 256)
  return `background-color: rgb(${red}, ${green}, ${blue})`
}

export default {
  name: 'List',
  props: {
    items: Array
  },
  methods: {
    _generateBackgroundColor
  },
  components: {
    ItemList
  }
}
</script>

<style lang="scss" scoped>
  section {
    display: grid;
	  grid-template-columns: repeat(auto-fill, 180px);
    justify-content: center;
  }
</style>