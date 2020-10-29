<template>
  <canvas ref="plot" id="plotting-canvas" width="500" height="500"></canvas>
</template>

<script>
export default {
  name: "PlottingCanvas",
  methods: {
    clear() {
      if (this.$refs.plot) {
        const { width, height } = this.$refs.plot;
        const ctx = this.$refs.plot.getContext("2d");
        ctx.clearRect(0, 0, width, height);
      }
    },
    resize() {
      if (this.$refs.plot && window) {
        this.$refs.plot.width = window.innerWidth;
        this.$refs.plot.height = window.innerHeight;
      }
    },
  },
  mounted() {
    this.clear();
    this.resize();
  },
  created() {
    if (window) {
      window.addEventListener("resize", this.resize);
    }
  },
  beforeDestroy() {
    if (window) {
      window.removeEventListener("resize", this.resize);
    }
  },
};
</script>

<style lang="stylus" scoped>
#plotting-canvas
  cursor crosshair
  position fixed
</style>
