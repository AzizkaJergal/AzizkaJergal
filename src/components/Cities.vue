<template>
<div>
  <div class="cities" :key="city.timezone" v-for="city in cities">
    <City :city="city" :utc="utc" />
  </div>
  </div>
</template>

<script>
import City from './City.vue';

export default {
  name: "Cities",
  props: {
      cities: Array,
      utc: Number
  },
  components: {
      City
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
