<template>
  <div id="app">
    <!-- TODO: MAKE TRANSLATIONS ONE STEP RATHER THAN EACH SCROLL TICK -->
    <h1 id="y"> {{ position[1] }}</h1>
    <h1 id="water-x"> {{ bottomWaterRight }}</h1>
    <div id="curtain" :style="{ top: curtainTop }"></div>
    <div id="white" :style="{ top: whiteTop }"></div>
    <img id="header" src="./assets/CS_Logo.png" alt="Coffee Syndicate Logo" />
    <img id="knob" src="./assets/knob.png" alt="knob" :style="{ transform: translateString(0, knobTop, knobRotation) }" />
    <img id="spout" src="./assets/spout.png" alt="spout" :style="{ transform: translateString(0, spoutTop), msTransform: translateString(0, spoutTop), webkitTransform: translateString(0, spoutTop) }" />
    <img id="water" src="./assets/water.png" alt="water" :style="{ transform: translateString(0, waterTop), msTransform: translateString(0, waterTop), webkitTransform: translateString(0, waterTop) }" />
    <img id="bottom-water" src="./assets/bottom_water.svg" alt="bottom-water"
      :style="{ transform: translateString(bottomWaterRight, bottomWaterTop), msTransform: translateString(bottomWaterRight, bottomWaterTop), webkitTransform: translateString(bottomWaterRight, bottomWaterTop) }" />
    <div id="content" :class="position[1] >= 13500 ? 'fadein' : 'fadeout'" :style="{ top: contentTop }">
      <h1 id="about-header">COFFEE SYNDICATE OFFERS WORLD CLASS COFFEE EQUIPMENT SERVICE, SALES & CUSTOM SOFTWARE
        SOLUTIONS</h1>
    </div>
  </div>
</template>

<script>
import windowScrollPosition from "./window-scroll-position";

export default {
  mixins: [windowScrollPosition("position")],
  name: "App",
  components: {},
  data() {
    return {
      curtainTop: 0+ "px",
      spoutTop: 200+ "px",
      knobTop: 20+ "px",
      waterTop: window.innerHeight * 1.5+ "px",
      bottomWaterTop: window.innerHeight * 1.5 + 900+ "px",
      bottomWaterRight: -200 + "%",
      knobRotation: 0+"deg",
      whiteTop: -100000+"px",
      contentTop: 300+"px",
      contentRight: 0+"px"
    };
  },
  methods: {
    translateString(x = '0px', y ='0px', angle = '0deg') {
      return `translate(${x}, ${y}) rotate(${angle})`
    }
  },
  computed: {
    scrollAmount() {
      return window.scrollY;
    },
    _curtainTop() {
      if (this.position[1] > 5000)
        return (-this.position[1] + 5000) / 8 + "px";
      else
        return 0 + "px";
    },
    _spoutTop() {
      if (this.position[1] > 5000)
        return (-this.position[1] + 5000) / 8 + 200 + "px";
      else
        return 200 + "px";
    },
    _knobTop() {
      if (this.position[1] > 5000)
        return (-this.position[1] + 5000) / 8 + 20 + "px"; 
      else
        return 20 + "px";
    },
    _waterTop() {
      if (this.position[1] > 5000)
        return (this.position[1]) / 28 - 900 + "px";
      else
        return window.innerHeight * 1.5 + "px";
    },
    _bottomWaterTop() {
      if (this.position[1] > 7000)
        return (-this.position[1] + 7000) / 6 + (window.innerHeight * 1.5) + "px";
      else
        return (window.innerHeight * 1.5) + 900 + "px";
    },
   _bottomWaterRight() {
      if (this.position[1] > 10000)
        return (this.position[1] - 15000) / 8 + "px";
      else
        return -200 + "%";
    },
    _knobRotation() {
      return this.position[1] / 80 + "deg";
    },
    _whiteTop() {
      return (15000 - this.position[1]) / 6 + "px";
    },
    _contentTop() {
      return (15000 - this.position[1]) / 6 + 300 + "px";
    },
    _contentRight() {
      return (15000 - this.position[1]) / 7 + "px";
    },
  },
  watch: {
    _curtainTop(val) {
      this.curtainTop = val;
    },
    _spoutTop(val) {
      this.spoutTop = val;
    },
    _knobTop(val) {
      this.knobTop = val;
    },
    _waterTop(val) {
      this.waterTop = val;
    },
    _bottomWaterTop(val) {
      this.bottomWaterTop = val;
    },
    _bottomWaterRight(val) {
      this.bottomWaterRight = val;
    },
    _knobRotation(val) {
      this.knobRotation = val;
    },
    _whiteTop(val) {
      this.whiteTop = val;
    },
    _contentTop(val) {
      this.contentTop = val;
    },
    _contentRight(val) {
      this.contentRight = val;
    },
  }
};
</script>

<style>
body {
  margin: 0;
  padding: 0;
  font-family: sans-serif;
  overscroll-behavior: none;
  background: #002b49;
}

#app {
  display: flex;
  flex-direction: column;
  height: 15500px;
  background: linear-gradient(180deg, #002b49 0%, #002b49 50%, #002947 100%);
}

#curtain {
  position: fixed;
  width: 100%;
  height: 820px;
  background: #002b49;
  z-index: 2;
  transition: top 0s linear;
  -moz-transition: -moz-transform 0s linear;
  -ms-transition: -ms-transform 0s linear;
  -webkit-transition: -webkit-transform 0s linear;
}

#white {
  background: linear-gradient(180deg, #ffffff 0%, #ffffff 50%, #fafafa 100%);
  width: 100%;
  height: 1500px;
  position: fixed;
  left: 0;
  z-index: 5;
  transition: top 0s linear;
  -moz-transition: -moz-transform 0s linear;
  -ms-transition: -ms-transform 0s linear;
  -webkit-transition: -webkit-transform 0s linear;
}

#y {
  position: fixed;
  top: 0;
  right: 0;
  color: white;
  font-size: 20px;
  padding: 10px;
  z-index: 10;
  transition: top 0s linear;
  -moz-transition: -moz-transform 0s linear;
  -ms-transition: -ms-transform 0s linear;
  -webkit-transition: -webkit-transform 0s linear;
}

#water-x {
  position: fixed;
  top: 30px;
  right: 0;
  color: white;
  font-size: 20px;
  padding: 10px;
  z-index: 10;
  transition: top 0s linear;
  -moz-transition: -moz-transform 0s linear;
  -ms-transition: -ms-transform 0s linear;
  -webkit-transition: -webkit-transform 0s linear;
}

#header {
  position: fixed;
  width: 250px;
  top: 15px;
  left: calc(50% - 125px);
  z-index: 10;
  filter: invert(0);
  mix-blend-mode: difference;
  transition: top 0s linear;
  -moz-transition: -moz-transform 0s linear;
  -ms-transition: -ms-transform 0s linear;
  -webkit-transition: -webkit-transform 0s linear;
}

#spout {
  position: fixed;
  width: 300px;
  left: 56px;
  z-index: 3;
  transition: top 0s linear;
  -moz-transition: -moz-transform 0s linear;
  -ms-transition: -ms-transform 0s linear;
  -webkit-transition: -webkit-transform 0s linear;
}

#knob {
  position: fixed;
  width: 225px;
  left: 0;
  z-index: 4;
  transition: top 0s linear;
  -moz-transition: -moz-transform 0s linear;
  -ms-transition: -ms-transform 0s linear;
  -webkit-transition: -webkit-transform 0s linear;
}

#water {
  position: fixed;
  width: 100px;
  left: 250px;
  z-index: 1;
  transition: top 0s linear;
  -moz-transition: -moz-transform 0s linear;
  -ms-transition: -ms-transform 0s linear;
  -webkit-transition: -webkit-transform 0s linear;
}

#bottom-water {
  position: fixed;
  width: 300%;
  z-index: 1;
  transition: top 0s linear;
  -moz-transition: -moz-transform 0s linear;
  -ms-transition: -ms-transform 0s linear;
  -webkit-transition: -webkit-transform 0s linear;
}

#about-header {
  position: fixed;
  width: 80%;
  left: 10%;
  margin-top: 300px;
  color: #002b49;
  padding: 10px;
  text-align: center;
  transition: top 0s linear;
  -moz-transition: -moz-transform 0s linear;
  -ms-transition: -ms-transform 0s linear;
  -webkit-transition: -webkit-transform 0s linear;
}

#content {
  width: 100%;
  transition: opacity .5s ease-in-out;
  z-index: 10;
}

.fadeout {
  opacity: 0;
}

.fadein {
  opacity: 1;
}</style>
