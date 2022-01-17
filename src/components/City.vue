<template>
  <div class="city">
    <h2>{{ city.name }}, {{ city.timezone }}</h2>
    <h3>{{convertUTCToTz(utc, city.offset)}}</h3>
  </div>
</template>

<script>
export default {
  name: "City",
  data() {
    return { date: null };
  },
  props: {
    city: Object, 
    utc: Number
  },
  methods: {
    convertUTCToTz(utc, offset) {
      const newTimeStr = utc + 3600000 * offset;
      return new Date(newTimeStr);
    }
  },
  created() {
    this.convertUTCToTz(this.utc, this.city.offset)
  }
};
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
