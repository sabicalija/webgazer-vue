<template>
  <div>
    <CalibrationPoint
      v-for="count of 9"
      :key="count"
      :id="`pt${count}`"
      width="31vw"
      height="29vh"
      :max="repetitions"
      :x="x"
      :y="y"
      :horizontal="count % 3 === 2 ? true : false"
      :vertical="count <= 6 && count > 3 ? true : false"
      :top="calcTop(count)"
      :left="calcLeft(count)"
      :right="calcRight(count)"
      :bottom="calcBottom(count)"
      @click="onClick"
      @create="onCreate"
    />
  </div>
</template>

<script>
import CalibrationPoint from "@/components/CalibrationPoint.vue";
export default {
  name: "CalibrationPoints",
  components: { CalibrationPoint },
  props: {
    x: {
      type: Number,
      default: 0,
    },
    y: {
      type: Number,
      default: 0,
    },
  },
  data() {
    return {
      repetitions: 5,
      points: {},
      calibrated: false,
    };
  },
  methods: {
    onClick(id) {
      this.points[id] += 1;
      if (typeof Object.values(this.points).find((e) => e < this.repetitions) === "undefined") {
        this.calibrated = true;
      }
    },
    onCreate(id) {
      this.points[id] = 0;
    },
    calcTop(index) {
      if (index <= 3) return "2vw";
      else if (index <= 6) return "50vh";
      return "unset";
    },
    calcLeft(index) {
      if (index % 3 === 1) return "2vw";
      else if (index % 3 === 2) return "50vw";
      return "unset";
    },
    calcRight(index) {
      if (index % 3 === 0) return "2vw";
      return "unset";
    },
    calcBottom(index) {
      if (index > 6) return "2vw";
      return "unset";
    },
  },
};
</script>

<style lang="stylus" scoped></style>
