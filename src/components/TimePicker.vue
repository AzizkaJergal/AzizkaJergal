<template>
  <div class="hello">
    <form class="add-form">
    
    <div class="form-control">
      <label>Please pick a time: </label>
      <input
        type="time"
        v-model="time"
        name="time-picker"
        placeholder="Add Time"
        @change="$emit('parse-time', time)"
      />
    </div>

  </form>
  </div>
</template>

<script>

export default {
  name: "TimePicker",
  data() {
    return {
      time: ""
    }
  },
  props: {
      utc: Number
  },
  created() {
    console.log("inside timepicker= ",this.utc);
    let date = new Date(this.utc);
    let localOffset = date.getTimezoneOffset() * 60000;
    date = new Date(this.utc - localOffset);
    let hours = date.getHours();
    let minutes = date.getMinutes();
    let minuteStr = minutes < 10 ? `0${minutes}` : minutes;
    let hourStr = hours < 10 ? `0${hours}` : hours;
    this.time = hourStr + ":" + minuteStr;
  },
  emits: ['parse-time']
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
