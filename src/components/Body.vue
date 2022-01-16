<script>
import Dancer from "./Dancer.vue";
import DencerMan from "../DencerMan";
import StyleDance from "../StyleDance.js";
export default {
  components: {
    Dancer,
  },
  props: {
    currentStyleDance: {
      type: StyleDance,
    },
  },
  data() {
    return {
      dancers: [],
    };
  },
  computed: {
    drinkingDencer() {
      return this.dancers.filter((dancer) => {
        return dancer.styleMusics.every(
          (styleMusic) => styleMusic !== this.currentStyleDance.styleName
        );
      });
    },
  },
  mounted() {
    this.dancers = [
      new DencerMan("Alex", "man", ["rnb", "Hip-hop"]),
      new DencerMan("Anna", "female", ["Electrohouse", "house"]),
      new DencerMan("Mark", "female", ["Pop"]),
    ];
  },
};
</script>
<template>
  <div class="wrapper-bar">
    <div class="dance-floor" v-if="dancers.length">
      <Dancer
        v-for="(dancer, index) in dancers"
        :key="index"
        :dancer="dancer"
        :currentStyleDance="currentStyleDance"
        :drinkingDencer="drinkingDencer"
      />
    </div>
    <div class="bar-table">Bar</div>
  </div>
</template>

<style lang="scss" scoped>
.wrapper-bar {
  background-color: rgb(192, 170, 180);
  height: calc(100vh - 100px);
  display: flex;
  .dance-floor {
    background-color: rgb(177, 170, 192);
    height: 100%;
    width: 80%;
    display: flex;
    position: relative;
  }
  .bar-table {
    background-color: rgb(72, 21, 184);
    height: 100%;
    width: 20%;
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
    font-size: 40px;
  }
}
</style>
