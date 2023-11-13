<template>
  <div id="app">
    <div id="curtain" :style="{ top: curtainTop }"></div>
    <h1 id="y">{{ position[1] }}</h1>
    <div id="white" :style="{ top: whiteTop }"></div>
    <div id="circular-wrapper" @click="openContact()" :class="position[1] >= 8800 ? 'show' : 'hide'">
      <img id="circular-1" src="./assets/circular-01.png">
      <img id="circular-2" src="./assets/circular-02.png">
    </div>
    <img id="header" src="./assets/Coffee Syndicate Logo Full.svg" alt="Coffee Syndicate Logo" />
    <img id="knob" src="./assets/knob.png" alt="knob" :style="{ transform: translateString(0, knobTop, knobRotation) }" />
    <img id="spout" src="./assets/spout.png" alt="spout" :style="{ transform: translateString(0, spoutTop) }" />
    <img id="water" src="./assets/water.png" alt="water" :style="{ transform: translateString(0, waterTop) }" />
    <img id="bottom-water" src="./assets/bottom_water.svg" alt="bottom-water"
      :style="{ transform: translateString(bottomWaterRight, bottomWaterTop) }" />
    <div id="content" :style="{ top: contentTop }" :class="position[1] >= 8800 ? 'show' : 'hide'">
      <h1 id="about-header">coffee syndicate offers coffee equipment sales, service and custom software solutions to the
        salt lake valley and beyond.</h1>
      <div id="blocks" :style="{transform: translateString(0, blocksBottom)}">
        <div class="block">
          <h2>sales</h2>
          <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Nulla minima illum ab officia non quod quas, exercitationem vel iure corrupti nihil sequi blanditiis inventore. Accusamus ex doloribus iste reiciendis eveniet.</p></div>
        <div class="block">
          <h2>service</h2>
          <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Excepturi doloribus minima cum nemo aliquam sit iste suscipit ex molestias ducimus laudantium delectus deleniti aliquid, nulla neque obcaecati sunt ipsum tenetur!</p></div>
        <div class="block">
          <h2>software</h2>
          <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Rem adipisci qui hic aperiam ad consectetur, praesentium quis corrupti blanditiis sunt magnam tempora nobis, aliquid repudiandae placeat iure laborum accusamus est.</p></div>
      </div>
    </div>
  </div>
</template>

<script>
import windowScrollPosition from "./window-scroll-position";

export default {
  mixins: [windowScrollPosition("position")],
  name: "App",
  components: {},
  mounted() {
    for (let i = 0; i < 15500; i++)
      setTimeout(() => {
        window.scrollTo(0, i);
      }, i * 0.5);
  },
  data() {
    return {
      curtainTop: 0 + "px",
      spoutTop: 200 + "px",
      knobTop: 20 + "px",
      waterTop: window.innerHeight * 1.5 + "px",
      bottomWaterTop: window.innerHeight * 1.5 + 900 + "px",
      bottomWaterRight: -200 + "%",
      knobRotation: 0 + "deg",
      whiteTop: -100000 + "px",
      contentTop: 300 + "px",
      contentRight: 0 + "px",
      blocksBottom: window.innerHeight * 1.5 + 300 + "px"
    };
  },
  methods: {
    translateString(x = '0px', y = '0px', angle = '0deg') {
      return `translate3d(${x}, ${y}, 0) rotate(${angle})`;
    },
    openContact() {
      window.open("https://www.coffeesyndicate.com/contact", "_blank");
    }
  },
  watch: {
    position(val) {
      console.log(val);
      if (this.position[1] > 5000)
        this.curtainTop = (-this.position[1] + 5000) / 8 + "px";
      else
        this.curtainTop = 0 + "px";
      if (this.position[1] > 5000)
        this.spoutTop = (-this.position[1] + 5000) / 8 + 200 + "px";
      else
        this.spoutTop = 200 + "px";
      if (this.position[1] > 5000)
        this.knobTop = (-this.position[1] + 5000) / 8 + 20 + "px";
      else
        this.knobTop = 20 + "px";
      if (this.position[1] > 5000) {
        this.waterTop = (this.position[1]) / 28 - 900 + "px";
      this.blocksBottom = (this.position[1] - 15500) / 28 - 900 + "px";
      }
      else {
        this.waterTop = window.innerHeight * 1.5 + "px";
        this.blocksBottom = window.innerHeight * 1.5 + "px";
      }
      if (this.position[1] > 6000)
        this.bottomWaterTop = (-this.position[1] + 6000) / 6 + (window.innerHeight * 1.5) + "px";
      else
        this.bottomWaterTop = (window.innerHeight * 1.5) + 900 + "px";
      if (this.position[1] > 8000)
        this.bottomWaterRight = (8000 - this.position[1]) / 8 + "px";
      else
        this.bottomWaterRight = -200 + "%";
      this.knobRotation = this.position[1] / 80 + "deg";
      this.whiteTop = (15000 - this.position[1]) / 6 + "px";
      this.contentTop = (15000 - this.position[1]) / 6 + 300 + "px";
      this.contentRight = (15000 - this.position[1]) / 7 + "px";
    }
  }
};
</script>

<style>
@font-face {
  font-family: 'Manufaktur';
  src: url('./assets/Manufaktur-Expanded-Bold.woff') format('woff'),
}

body {
  margin: 0;
  padding: 0;
  font-family: sans-serif;
  overscroll-behavior: none;
  background: #002b49;
}

h1,
h2,
h3,
h4,
h5,
h6,
p {
  font-family: 'Manufaktur', sans-serif;
}

h1 {
  font-size: 20px;
}

#app {
  display: flex;
  flex-direction: column;
  height: 15500px;
  background: #002b49;
}

#curtain {
  position: fixed;
  width: 100%;
  height: 820px;
  background: #002b49;
  z-index: 2;
  transition: top .02s linear;
  -moz-transition: -moz-transform .02s linear;
  -ms-transition: -ms-transform .02s linear;
  -webkit-transition: -webkit-transform .02s linear;
}

#white {
  background: linear-gradient(180deg, #ffffff 0%, #ffffff 50%, #fafafa 100%);
  width: 100%;
  height: 1500px;
  position: fixed;
  left: 0;
  z-index: 5;
  transition: top .02s linear;
  -moz-transition: -moz-transform .02s linear;
  -ms-transition: -ms-transform .02s linear;
  -webkit-transition: -webkit-transform .02s linear;
}

#y {
  position: fixed;
  top: 0;
  right: 0;
  color: white;
  font-size: 20px;
  padding: 10px;
  z-index: 10;
  transition: top .02s linear;
  -moz-transition: -moz-transform .02s linear;
  -ms-transition: -ms-transform .02s linear;
  -webkit-transition: -webkit-transform .02s linear;
}

#water-x {
  position: fixed;
  top: 30px;
  right: 0;
  color: white;
  font-size: 20px;
  padding: 10px;
  z-index: 10;
  transition: top .02s linear;
  -moz-transition: -moz-transform .02s linear;
  -ms-transition: -ms-transform .02s linear;
  -webkit-transition: -webkit-transform .02s linear;
}

#header {
  position: fixed;
  width: 250px;
  top: 15px;
  left: calc(50% - 125px);
  z-index: 10;
  filter: invert(0);
  mix-blend-mode: difference;
  transition: top .02s linear;
  -moz-transition: -moz-transform .02s linear;
  -ms-transition: -ms-transform .02s linear;
  -webkit-transition: -webkit-transform .02s linear;
}

#spout {
  position: fixed;
  width: 300px;
  left: 56px;
  z-index: 3;
  transition: top .02s linear;
  -moz-transition: -moz-transform .02s linear;
  -ms-transition: -ms-transform .02s linear;
  -webkit-transition: -webkit-transform .02s linear;
}

#knob {
  position: fixed;
  width: 225px;
  left: 0;
  z-index: 4;
  transition: top .02s linear;
  -moz-transition: -moz-transform .02s linear;
  -ms-transition: -ms-transform .02s linear;
  -webkit-transition: -webkit-transform .02s linear;
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
  transition: top .02s linear;
  -moz-transition: -moz-transform .02s linear;
  -ms-transition: -ms-transform .02s linear;
  -webkit-transition: -webkit-transform .02s linear;
}

#about-header {
  position: fixed;
  width: 50%;
  left: 25%;
  margin-top: 300px;
  color: #002b49;
  padding: 10px;
  text-align: center;
  transition: .02s linear;
  -moz-transition: -moz-transform .02s linear;
  -ms-transition: -ms-transform .02s ease-in-out;
  -webkit-transition: -webkit-transform .02s ease-in-out;
}

#content {
  width: 100%;
  transition: opacity .2s ease-in-out;
  text-align: center;
  z-index: 10;
}

#circular-wrapper {
  position: fixed;
  width: 250px;
  height: 250px;
  bottom: 15px;
  right: 14px;
  z-index: 10;
}

#circular-1 {
  width: 100%;
  position: absolute;
  top: 0;
  left: 0;
}

#circular-2 {
  transition: top .02s linear;
  -moz-transition: -moz-transform .02s linear;
  -ms-transition: -ms-transform .02s linear;
  -webkit-transition: -webkit-transform .02s linear;
  animation: rotate 8s linear infinite;
  width: 100%;
  position: absolute;
  top: 0;
  left: 0;
}

#circular-1:hover,
#circular-2:hover {
  animation-play-state: paused;
  /* Add this line */
  cursor: pointer;
  opacity: .8;
}

#blocks {
  display: flex;
  flex-direction: row;
  width: 75%;
  height: 25%;
  position: fixed;
  bottom: 50px;
}

.show {

}

.hide {
  display: none;
}

.block {
  margin: 15px;
  display: block;
  text-align: left;
  color: #002b49;
}

.filter {
  animation: filter 2s;
}

@keyframes filter {
  from {
      filter: none;
  }
  to {
      filter: invert(0);
      mix-blend-mode: difference;
  }
}

@keyframes rotate {
  from {
    transform: rotate(0deg);
  }

  to {
    transform: rotate(360deg);
  }
}

.fadeout {
  opacity: 0;
}

.fadein {
  opacity: 1;
}</style>
