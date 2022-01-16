<script>
import DencerMan from "../DencerMan.js";
import StyleDance from "../StyleDance.js";
export default {
  props: {
    dancer: {
      type: DencerMan,
      require: true,
    },
    currentStyleDance: {
      type: StyleDance,
    },
    drinkingDencer: {
      type: Array,
    },
  },
  data() {
    return {
      time: 3,
      drinkStyleDance: {
        styleName: "rnb",
        bodyTopDance: "bodyTopDance-Drink",
        headDance: "headDance-Drink",
        firstHandLeft: "firstHandLeft-Drink",
        firstHandRight: "firstHandRight-Drink",
        secondHandLeft: "secondHandLeft-Drink",
        secondHandRight: "secondHandRight-Drink",
        firstLegRight: "firstLegRight-Drink",
        secondLegRight: "secondLegRight-Drink",
        stepLegRight: "stepLegRight-Drink",
        firstLegLeft: "firstLegLeft-Drink",
        secondLegLeft: "secondLegLeft-Drink",
        stepLegLeft: "stepLegLeft-Drink",
      },
    };
  },
  computed: {
    correctStyleDance() {
      return this.someStyleDance
        ? this.currentStyleDance
        : this.drinkStyleDance;
    },
    animationDurationHead() {
      return `${this.time * 0.5}s`;
    },
    animationDurationPartBody() {
      return `${this.time}s`;
    },
    faceHead() {
      return this.dancer.gender === "man"
        ? require("@/assets/images/svg/man.svg")
        : require("@/assets/images/svg/female.svg");
    },
    torsoImg() {
      return this.dancer.gender === "man"
        ? require("@/assets/images/svg/t_shirt.svg")
        : require("@/assets/images/svg/dress.svg");
    },
    someStyleDance() {
      return this.dancer.styleMusics.some((styleMusic) => {
        return styleMusic === this.currentStyleDance.styleName;
      });
    },
    getIndexByArrayDrinkers() {
      return this.drinkingDencer.findIndex((drinkdencer) => {
        return drinkdencer === this.dancer;
      });
    },
  },
  mounted() {
    setTimeout(() => {
      console.log(this.index);
    }, 3000);
  },
};
</script>
<template>
  <div
    class="box-dancer"
    :class="{ drink: !someStyleDance }"
    :style="{ bottom: `${getIndexByArrayDrinkers * 200}px` }"
  >
    <div class="body-footer">
      <div
        class="body-top"
        :style="{
          'animation-duration': animationDurationPartBody,
          'animation-name': correctStyleDance
            ? correctStyleDance.bodyTopDance
            : '',
        }"
      >
        <img class="torsoImg" :src="torsoImg" alt="torso" />
        <div
          class="part-body head"
          :style="{
            'animation-duration': animationDurationHead,
            'animation-name': correctStyleDance
              ? correctStyleDance.headDance
              : '',
          }"
        >
          <img :src="faceHead" alt="face" />
        </div>
        <div
          class="part-body first-hand first-hand-left"
          :style="{
            'animation-duration': animationDurationPartBody,
            'animation-name': correctStyleDance
              ? correctStyleDance.firstHandLeft
              : '',
          }"
        >
          <div
            class="part-body second-hand second-hand-left"
            :style="{
              'animation-duration': animationDurationPartBody,
              'animation-name': correctStyleDance
                ? correctStyleDance.secondHandLeft
                : '',
            }"
          ></div>
        </div>
        <div
          class="part-body first-hand first-hand-right"
          :style="{
            'animation-duration': animationDurationPartBody,
            'animation-name': correctStyleDance
              ? correctStyleDance.firstHandRight
              : '',
          }"
        >
          <div
            class="part-body second-hand second-hand-right"
            :style="{
              'animation-duration': animationDurationPartBody,
              'animation-name': correctStyleDance
                ? correctStyleDance.secondHandRight
                : '',
            }"
          >
            <img
              v-if="!someStyleDance"
              class="vodka"
              src="@/assets/images/svg/vodka.svg"
              alt="vodka"
            />
          </div>
        </div>
      </div>
      <div
        class="part-body first-leg first-leg-left"
        :style="{
          'animation-duration': animationDurationPartBody,
          'animation-name': correctStyleDance
            ? correctStyleDance.firstLegLeft
            : '',
        }"
      >
        <div
          class="part-body second-leg second-leg-left"
          :style="{
            'animation-duration': animationDurationPartBody,
            'animation-name': correctStyleDance
              ? correctStyleDance.secondLegLeft
              : '',
          }"
        >
          <div
            class="part-body step step-left"
            :style="{
              'animation-duration': animationDurationPartBody,
              'animation-name': correctStyleDance
                ? correctStyleDance.stepLegLeft
                : '',
            }"
          ></div>
        </div>
      </div>
      <div
        class="part-body first-leg first-leg-right"
        :style="{
          'animation-duration': animationDurationPartBody,
          'animation-name': correctStyleDance
            ? correctStyleDance.firstLegRight
            : '',
        }"
      >
        <div
          class="part-body second-leg second-leg-right"
          :style="{
            'animation-duration': animationDurationPartBody,
            'animation-name': correctStyleDance
              ? correctStyleDance.secondLegRight
              : '',
          }"
        >
          <div
            class="part-body step step-right"
            :style="{
              'animation-duration': animationDurationPartBody,
              'animation-name': correctStyleDance
                ? correctStyleDance.stepLegRight
                : '',
            }"
          ></div>
        </div>
      </div>
    </div>
  </div>
</template>
<style lang="scss">
@import "../styles/keyframesRnbHipHop.scss";
@import "../styles/keyframesElectrodanceHouse.scss";
@import "../styles/keyframesDrink.scss";
@import "../styles/keyframesPop.scss";

@keyframes drinkAnimation {
  0% {
    bottom: 200px;
    right: 200px;
  }
  100% {
    bottom: 0px;
    right: 0px;
  }
}
.drink {
  bottom: 0px;
  right: 0px;
  position: absolute !important;
  animation-name: drinkAnimation;
  animation-duration: 1s;
}
.box-dancer {
  margin: 10px;
  height: 500px;
  width: 300px;
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  .body-footer {
    position: relative;
    width: 5px;
    height: 5px;
    .part-body {
      position: absolute;
      width: 5px;
      background-color: black;
      animation-iteration-count: infinite;
    }
    .body-top {
      bottom: 1px;
      width: 5px;
      height: 100px;
      background-color: black;
      position: absolute;
      animation-iteration-count: infinite;
      transform-origin: 100% 100%;
      transform: rotate(0deg);
      z-index: 1;
      .torsoImg {
        position: absolute;
        top: -10px;
        left: -81px;
        height: 160px;
        z-index: 10;
      }
      .head {
        height: 50px;
        width: 50px;
        top: -50px;
        left: -25px;
        border-radius: 50%;
        transform-origin: 0% 70%;
        transform: rotate(0deg);
        background-color: transparent;
        img {
          height: 60px;
        }
      }
      .first-hand {
        height: 100px;
        transform-origin: 0% 0%;
        .second-hand {
          height: 100px;
          transform-origin: 0% 100%;
        }
      }
      .first-hand-left {
        transform: rotate(45deg);
        .second-hand-left {
          transform: rotate(-60deg);
        }
      }
      .first-hand-right {
        transform: rotate(-45deg);
        .second-hand-right {
          transform: rotate(60deg);
          .vodka {
            position: relative;
            top: -30px;
            right: 30px;
            height: 50px;
            transform: rotate(-90deg);
          }
        }
      }
    }

    .first-leg {
      height: 100px;
      transform-origin: 0% 0%;
      z-index: 0;
      .second-leg {
        height: 100px;
        transform-origin: 0% 100%;
        .step {
          height: 30px;
          transform-origin: 0% 0%;
        }
      }
    }
    .first-leg-right {
      transform: rotate(-40deg);
      .second-leg-right {
        transform: rotate(220deg);
        .step-right {
          transform: rotate(90deg);
        }
      }
    }
    .first-leg-left {
      transform: rotate(40deg);
      .second-leg-left {
        transform: rotate(-220deg);
        .step-left {
          transform: rotate(-90deg);
        }
      }
    }
  }
}
</style>
