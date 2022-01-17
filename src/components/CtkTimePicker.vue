<template>
  <div class="hello">
    <p>Please pick a time:</p>
    <input type="button" name="test" @click="handleClick()" />
    <VueCtkDateTimePicker
      v-model="time"
      format="hh:mm a"
      inputSize="sm"
      onlyTime
      noLabel
      color="fireBrick"
      @input="handleChange()"
      noButton
      output-format="hh:mm:ss"
    >
    </VueCtkDateTimePicker>

    <div>
      <div></div>
    </div>
    {{ time }}
  </div>
</template>

<script>
import VueCtkDateTimePicker from "vue-ctk-date-time-picker";
import "vue-ctk-date-time-picker/dist/vue-ctk-date-time-picker.css";

export default {
  name: "CtkTimePicker",
  components: { VueCtkDateTimePicker },
  data() {
    return {
      time: null,
    };
  },
  created() {
    let date = new Date();
    this.time = date;

  },
  methods: {
    handleChange() {
      console.log("changed!" + new Date(this.time));
    },
    handleClick() {
      console.log("clicked!");
    }
  },
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
