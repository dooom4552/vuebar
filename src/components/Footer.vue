<script>
export default {
  props: {
    styleDanceArrey: {
      type: Array,
    },
  },
  methods: {
    chooseStyleDance(styleDance) {
      this.$emit("chooseStyleDance", styleDance);
    },
  },
};
</script>
<template>
  <div class="footer-bar">
    <button
      v-for="(styleDance, index) in styleDanceArrey"
      :key="index"
      @click="chooseStyleDance(styleDance)"
    >
      {{ styleDance.styleName }}
    </button>
  </div>
</template>

<style lang="scss">
.footer-bar {
  background-color: rgb(174, 192, 170);
  height: 70px;
}
</style>
