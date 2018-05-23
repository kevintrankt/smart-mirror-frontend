// https://vuejsexamples.com/vue-component-for-draggable-and-resizable-elements/
<template>
  <div class="time">
        <VueDragResize :isActive="true" :w="400" :h="200" v-on:resizing="resize">
            <!-- <div class="drag">             -->
                <h1 v-bind:style="{fontSize:fontSizeScale+'px'}">{{hours}}:{{minutes}} {{hourtime}}</h1>
            <!-- </div> -->
        </VueDragResize>
  </div>
</template>

<script>
import { getHourTime, getZeroPad } from "./Filters";
import VueDragResize from "vue-drag-resize";

export default {
  name: "Time",
  components: {
    VueDragResize
  },
  data() {
    return {
      timeData: "blank",
      hours: "",
      minutes: "",
      seconds: "",
      hourtime: "",
      width: 0,
      height: 0,
      top: 0,
      left: 0,
      fontSizeScale: 70
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
    },
    resize(newRect) {
      this.width = newRect.width;
      this.height = newRect.height;
      this.top = newRect.top;
      this.left = newRect.left;
      this.fontSizeScale = this.width / 6;
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
  margin: 0;
  white-space: nowrap;
}

.drag {
  background-color: khaki;
  width: 100%;
  height: 100%;
}

.time {
  width: max-content;
}
</style>
