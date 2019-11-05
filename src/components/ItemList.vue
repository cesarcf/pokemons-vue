<template>
  <figure :style='background'>
    <img :src='url' :alt='name | capitalize' />
    <figcaption>{{ name | capitalize }}</figcaption>
  </figure>
</template>

<script>
export default {
  name: 'ItemList',
  props: {
    url: String,
    name: String,
    background: String
  },
  filters: {
    capitalize(value) {
      return value[0].toUpperCase() + value.slice(1)
    }
  }
}
</script>

<style lang="scss" scoped>
  figure {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 180px;
    height: 155px;
    margin: 0;

    img {
      max-width: 50px;
    }
  }
</style>