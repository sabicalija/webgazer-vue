<template>
  <div id="app">
    <WebGazer @update="onUpdate" :off="false" />
    <PlottingCanvas />
    <CalibrationPoints :x="x" :y="y" />
  </div>
</template>

<script>
import WebGazer from "@/components/WebGazer.vue";
import PlottingCanvas from "@/components/PlottingCanvas.vue";
import CalibrationPoints from "@/components/CalibrationPoints.vue";

export default {
  name: "App",
  components: { WebGazer, PlottingCanvas, CalibrationPoints },
  data() {
    return {
      x: 0,
      y: 0,
    };
  },
  methods: {
    onUpdate(coord) {
      this.x = coord.x;
      this.y = coord.y;
    },
  },
};
</script>

<style lang="stylus"></style>
