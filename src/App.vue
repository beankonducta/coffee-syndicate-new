<template>
  <div id="app">
    <h1 id="h-1" :style="{ top: h1Top }">
      Let's get that machine working again.
    </h1>
    <h1 id="y"> {{  position[1] }}</h1>
    <div v-if="position[1] <= 8500" id="bottom-curtain"></div>
    <div v-if="position[1] >= 8500" id="center-curtain"></div>
    <img
      id="header"
      src="./assets/Coffee Syndicate Logo Full.svg"
      alt="Coffee Syndicate Logo"
    />
    <img
      id="pf"
      src="./assets/icon-01.png"
      :style="{ top: pfTop, right: pfRight }"
      alt="Portafilter"
    />
    <img
      id="basket"
      src="./assets/icon-03.png"
      :style="{ top: basketTop, right: basketRight }"
      alt="Basket" 
    />
    <img
      id="coffee"
      src="./assets/icon-07.png"
      :style="{ top: coffeeTop, right: coffeeRight }"
      alt="Coffee"
    />
    <img
      id="puck"
      src="./assets/icon-02.png"
      :style="{ top: puckTop, right: puckRight, opacity: puckOpacity }"
      alt="Puck"
    />
    <img
      id="tamper"
      src="./assets/icon-05.png"
      :style="{ top: tamperTop, right: tamperRight }"
      alt="Tamper"
    />
    <img
      id="screw"
      src="./assets/icon-04.png"
      :style="{ top: screwTop, right: screwRight }"
      alt="Screw"
    />
    <img
      id="screen"
      src="./assets/icon-06.png"
      :style="{ top: screenTop, right: screenRight }"
      alt="Screen"
    />
    <img
      id="tube"
      src="./assets/icon-08.png"
      :style="{ top: tubeTop, right: tubeRight }"
      alt="Tube"
    />
    <img
      id="drip"
      src="./assets/icon-09.png"
      :style="{ top: dripTop, right: dripRight }"
      alt="Drip"
    />
    <img
      id="spro"
      v-if="position[1] >= 8500"
      src="./assets/icon-10.png"
      :style="{ top: sproTop, right: sproRight }"
      alt="Spro"
    />
  </div>
</template>

<script>
import windowScrollPosition from "./window-scroll-position";

export default {
  mixins: [windowScrollPosition("position")],
  name: "App",
  components: {},
  methods: {},
  computed: {
    scrollAmount() {
      return window.scrollY;
    },
    h1Top() {
      return window.innerHeight / 2 - this.position[1] + "px";
    },
    pfTop() {
      return window.innerHeight / 4 + "px";
    },
    pfRight() {
      let pos = -1000 + this.position[1];
      if (pos <= window.innerWidth / 2 - 500) {
        return pos + "px";
      } else {
        return window.innerWidth / 2 - 500 + "px";
      }
    },
    basketTop() {
      let pos = -1500 + this.position[1];
      if (pos <= +this.pfTop.replace("px", "")) {
        return pos + "px";
      } else {
        return this.pfTop;
      }
    },
    basketRight() {
      return window.innerWidth / 2 - 500 + "px";
    },
    coffeeTop() {
      let pos = -2800 + this.position[1];
      return pos + "px";
    },
    coffeeRight() {
      return window.innerWidth / 2 - 500 + "px";
    },
    puckTop() {
      let offset = this.position[1] >= 2600 ? (2600 - this.position[1]) / 15 : 0;
      if (offset < -40) {
        offset = -40;
      }
      let pos = +this.basketTop.replace("px", "") +50 + offset;
      return pos + "px";
    },
    puckRight() {
      return window.innerWidth / 2 - 500 + "px";
    },
    puckOpacity() {
      return this.position[1] >= 2600 ? (this.position[1] - 2600) / 140 : 0;
    },
    tamperTop() {
      let pos = -3700 + this.position[1];
      if(this.position[1] >= 3900)
       pos = 200;
      if(this.position[1] >= 5000)
        pos = 200 + (5000 - this.position[1])
      return pos + "px";
    },
    tamperRight() {
      return window.innerWidth / 2 - 500 + "px";
    },
    screwTop() {
      let pos = -6300 + this.position[1];
      if(this.position[1] >= 6500)
        pos = 200;
      return pos + "px";
    },
    screwRight() {
      return window.innerWidth / 2 - 500 + "px";
    },
    screenTop() {
      let pos = -6450 + this.position[1];
      if(this.position[1] >= 6650)
        pos = 200;
      return pos + "px";
    },
    screenRight() {
      return window.innerWidth / 2 - 500 + "px";
    },
    tubeTop() {
      let pos = -6600 + this.position[1];
      if(this.position[1] >= 6750)
        pos = 150;
      return pos + "px";
    },
    tubeRight() {
      return window.innerWidth / 2 - 500 + "px";
    },
    dripTop() {
      let pos = -7600 + this.position[1];
      return pos + "px";
    },
    dripRight() {
      return window.innerWidth / 2 - 500 + "px";
    },
    sproTop() {
      let pos = (this.position[1] -10000);
      return pos + "px";
    },
    sproRight() {
      return window.innerWidth / 2 - 500 + "px";
    },
  },
};
</script>

<style>
body {
  margin: 0;
  padding: 0;
  font-family: sans-serif;
  overscroll-behavior: none;
}

#app {
  display: flex;
  flex-direction: column;
  height: 15000px;
  background: #002b49;
}

#bottom-curtain {
  position: fixed;
  height: 40%;
  width: 100%;
  background: #002b49;
  top: 60%;
  z-index: 2;
}

#center-curtain {
  position: fixed;
  height: 66%;
  width: 100%;
  background: #002b49;
  top: 0%;
  z-index: 2;
}

#y {
  position: fixed;
  top: 0;
  right: 0;
  color: white;
  font-size: 20px;
  padding: 10px;
}

#h-1 {
  position: fixed;
  width: 100%;
  text-align: center;
}

#header {
  position: fixed;
  height: 200px;
  top: 15px;
  z-index: 10;
}

#pf {
  position: fixed;
  width: 600px;
  z-index: 3;
}

#basket {
  position: fixed;
  width: 600px;
  z-index: 3;
}

#coffee {
  position: fixed;
  width: 600px;
  z-index: 1;
}

#puck {
  position: fixed;
  width: 600px;
  z-index: 3;
}

#tamper {
  position: fixed;
  width: 600px;
  z-index: 3;
}

#screw {
  position: fixed;
  width: 600px;
  z-index: 3;
}

#screen {
  position: fixed;
  width: 600px;
  z-index: 3;
}

#tube {
  position: fixed;
  width: 600px;
  z-index: 3;
}

#drip {
  position: fixed;
  width: 600px;
  z-index: 1;
}

#spro {
  position: fixed;
  width: 600px;
  z-index: 1;
}
</style>
