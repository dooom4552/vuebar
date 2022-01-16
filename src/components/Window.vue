<script>
import Body from "./Body";
import Footer from "./Footer";
import StyleDance from "../StyleDance";
export default {
  components: {
    Body,
    Footer,
  },
  data() {
    return {
      styleDanceArrey: [],
      currentStyleDance: null,
    };
  },
  mounted() {
    this.styleDanceArrey = [
      new StyleDance(),
      new StyleDance(
        "Electrohouse",
        "bodyTopDance-ElectrodanceHouse",
        "headDance-ElectrodanceHouse",
        "firstHandLeft-ElectrodanceHouse",
        "firstHandRight-ElectrodanceHouse",
        "secondHandLeft-ElectrodanceHouse",
        "secondHandRight-ElectrodanceHouse",
        "firstLegRight-ElectrodanceHouse",
        "secondLegRight-ElectrodanceHouse",
        "stepLegRight-ElectrodanceHouse",
        "firstLegLeft-ElectrodanceHouse",
        "secondLegLeft-ElectrodanceHouse",
        "stepLegLeft-ElectrodanceHouse"
      ),
      new StyleDance(
        "Pop",
        "bodyTopDance-Pop",
        "headDance-Pop",
        "firstHandLeft-Pop",
        "firstHandRight-Pop",
        "secondHandLeft-Pop",
        "secondHandRight-Pop",
        "firstLegRight-Pop",
        "secondLegRight-Pop",
        "stepLegRight-Pop",
        "firstLegLeft-Pop",
        "secondLegLeft-Pop",
        "stepLegLeft-Pop"
      ),
    ];
    this.currentStyleDance = this.styleDanceArrey[0];
  },
  methods: {
    chooseStyleDance(styleDance) {
      this.currentStyleDance = styleDance;
    },
  },
};
</script>
<template>
  <div class="window-box">
    <Body :currentStyleDance="currentStyleDance" />
    <Footer
      :styleDanceArrey="styleDanceArrey"
      @chooseStyleDance="chooseStyleDance"
    />
  </div>
</template>
<style lang="scss" scoped></style>
