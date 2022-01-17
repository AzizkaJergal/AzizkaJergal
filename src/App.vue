<template>
  <div id="app">
    <TimePicker :utc="utc" @parse-time="parseTime" />
    <Cities :cities="cities" :utc="utc" />
  </div>
</template>

<script>
import TimePicker from './components/TimePicker.vue';
import Cities from './components/Cities.vue';

export default {
  name: "App",
  data(){
    return {
      utc: 0,
      cities: []
    }
  },
  components: {
    TimePicker,
    Cities
  },
  methods: {
    parseTime(time) {
      console.log("parsing time in App",time)
      const timeArr = time.split(":");
      let d = new Date();      
      d.setHours(timeArr[0], timeArr[1]);
      this.convertDateToUTC(d);
    },
    convertDateToUTC(date) {
      const localTime = date.getTime();
      const localOffset = date.getTimezoneOffset() * 60000;
      console.log("localOffset=" + localOffset);
      console.log("utc=",this.utc);
      this.utc = localTime + localOffset; 
    }
  },
  created() {
    const date = new Date();
    this.convertDateToUTC(date);
    this.cities = [
      {
        name: "Toronto", 
        timezone: "UTC/GMT -5 hours",
        offset: -5
      },
      {
        name: "Danmarkshavn",
        timezone: "GMT",
        offset: 0
      },
      {
        name: "Baku", 
        timezone: "UTC/GMT +4 hours",
        offset: 4
      }
    ]
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
