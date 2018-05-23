<template>
  <div class="time">
      <h1>{{hours}}:{{minutes}} {{hourtime}}</h1>
  </div>
</template>

<script>
import { getHourTime, getZeroPad } from "./Filters";

export default {
  name: "Time",
  data() {
    return {
      timeData: "blank",
      hours: "",
      minutes: "",
      seconds: "",
      hourtime: ""
    };
  },
  methods: {
    updateDateTime() {
      let now = new Date();
      this.hours = now.getHours();
      this.minutes = getZeroPad(now.getMinutes());
      this.seconds = getZeroPad(now.getSeconds());
      this.hourtime = getHourTime(this.hours);
      this.hours = this.hours % 12 || 12;
    }
  },

  mounted() {
    setInterval(this.updateDateTime, 1000);
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1 {
  font-size: 70px;
  margin: 0;
}
.time {
  width: max-content;
}
</style>
