<template>
  <div id="app">
    <!-- <h1 id="y">{{ position[1] }}</h1> -->
    <div id="upper">
      <h1 id="request-service">Request Service</h1>
      <img
        src="./assets/Coffee Syndicate Logo Full_SPLIT-01.svg"
        alt="logo-1"
        id="logo-1"
      />
      <img
        src="./assets/Coffee Syndicate Logo Full_SPLIT-02.svg"
        alt="logo-2"
        id="logo-2"
      />
      <img
        src="./assets/Coffee Syndicate Logo Full_SPLIT-03.svg"
        alt="logo-3"
        id="logo-3"
      />
      <img
      id="bottom-water"
      src="./assets/bottom_water.svg"
      alt="bottom-water"
      :style="{ marginLeft: waterLeft + 'px' }"
    />
    </div>
    <!-- <h1 id="about-header" :style="{ opacity: (400 - position[1]) / 400 }">
        Coffee Equipment Sales, Service & Software Solutions
      </h1> -->
    <div id="content">
      <!-- <div id="circular-wrapper" @click="openContact()">
        <img id="circular-1" src="./assets/circular-01.png" />
        <img id="circular-2" src="./assets/circular-02.png" />
      </div> -->
      <div class="blocks">
        <div class="block thirty">
          <h2>Sales</h2>
          <p>
            We distribute top-tier coffee & espresso equipment from brands we have first-hand
            experience with. We only offer equipment that we know will perform well and last
            for years to come. We also offer a wide range of accessories and smallwares to
            help you get the most out of your equipment.
            <br>
            <br>
            We offer full equipment packages, including installation and training, as well as
            individual equipment purchases. Financing or lease is available for qualified buyers.
          </p>
          <p class="reveal">Brands</p>
        </div>
        <div class="block thirty">
          <h2>Service</h2>
          <p>
            Even the best coffee equipment needs service and we're certified to work on
            the brands we sell. We also offer service on a wide range of other brands
            and can even perform emergency service after hours and on weekends or holidays.
            <br>
            <br>
            We also have experience working on industrial control systems, specifically in
            the realm of coffee roasters and packaging equipment.
          </p>
          <p class="reveal">Request Service</p>
        </div>
        <div class="block thirty">
          <h2>Software</h2>
          <p>
            We've developed custom software solutions to make the mundane tasks of running a 
            small business easier. Web apps we've made include a till and tip management system
            with Square integration, various order management and fulfillment tools, and even a 
            browser-based roasting software suite.
            <br>
            <br>
            We'd love to consult and see if there's a custom or prefab solution that we can integrate
            into your workflow to increase productivity.
          </p>
          <p class="reveal">More</p>
        </div>
      </div>
      <div class="blocks">
        <div class="block fifty">
          <h2>About</h2>
          <p>
           Coffee Syndicate spawned from years of tinkering with hardware and software. We've refurbished
           dozens of espresso machines, grinders, brewers, and have developed custom software for our own
           business use as well as for other small businesses. We're passionate about coffee and technology and
           the efficiencies that the marriage of the two can create.
          </p>
        </div>
      </div>
    </div>
    <div id="footer">
      &copy; Coffee Syndicate {{ new Date().getFullYear() }}
    </div>
  </div>
</template>

<script>
import windowScrollPosition from "./window-scroll-position";

export default {
  mixins: [windowScrollPosition("position")],
  name: "App",
  components: {},
  mounted() {},
  data() {
    return {
      waterLeft: 0,
    };
  },
  methods: {
    translateString(x = "0px", y = "0px", angle = "0deg") {
      return `translate3d(${x}, ${y}, 0) rotate(${angle})`;
    },
    openContact() {
      window.open("https://www.coffeesyndicate.com/contact", "_blank");
    },
  },
  watch: {
    position(val) {
      this.waterLeft = -window.innerWidth + val[1] / 2;
    },
  },
};
</script>

<style>
@font-face {
  font-family: "Manufaktur";
  src: url("./assets/Manufaktur-Expanded-Bold.woff") format("woff");
}

@font-face {
  font-family: "Prompt";
  src: url("./assets/Prompt-Medium.woff") format("woff");
}

body {
  margin: 0;
  padding: 0;
  font-family: sans-serif;
  background: #002b49;
  min-height: 80vh;
}

h1,
h2,
h3,
h4,
h5,
h6 {
  font-family: "Manufaktur", sans-serif;
}

h1 {
  font-size: 1rem;
}

p {
  font-size: 0.85rem;
  line-height: 1.5rem;
  font-family: "Prompt", sans-serif;
}


#app {
  background: #002b49;
  overflow-x: clip;
  min-height: 80vh;
}

#upper {
  background: #002b49;
  position: relative;
}

#footer {
  height: 15%;
  padding: 2%;
  color: white;
  background: #002b49;
  font-family: "Manufaktur", sans-serif;
  text-align: center;
}

#y {
  position: fixed;
  top: 0;
  right: 0;
  color: white;
  font-size: 20px;
  padding: 10px;
  z-index: 10;
  transition: top 0.02s linear;
  -moz-transition: -moz-transform 0.02s linear;
  -ms-transition: -ms-transform 0.02s linear;
  -webkit-transition: -webkit-transform 0.02s linear;
}

.reveal {
  font-family: "Manufaktur", sans-serif;
  bottom: -50px;
  position: absolute;
  color: #002b49;
  text-decoration: underline;
}

.reveal:hover {
  color: #ffa96d;
  cursor: pointer;
}

#logo-1 {
  z-index: 10;
  position: sticky;
  width: 50%;
  top: 25px;
  margin-left: 25%;
  filter: invert(1);
  mix-blend-mode: difference;
}

#logo-2 {
  z-index: 8;
  position: fixed;
  width: 50%;
  top: 25px;
  left: 25%;
  filter: invert(1);
  mix-blend-mode: difference;
}

#logo-3 {
  z-index: 11;
  position: sticky;
  width: 50%;
  top: 25px;
  margin-left: 25%;
}

#bottom-water {
  position: relative;
  width: 300%;
  margin-bottom: -3%;
  transition: left 0.02s linear;
  -moz-transition: -moz-transform 2s linear;
  -ms-transition: -ms-transform 2s linear;
  -webkit-transition: -webkit-transform 2s linear;
  z-index: 9;
}

#request-service {
  position: fixed;
  top: -1rem;
  right: 0;
  font-size: 1rem;
  padding: 0.5rem;
  border-radius: 0px 0px 0px 5px;
  color: white;
  filter: invert(1);
  mix-blend-mode: difference;
  z-index: 10;
  background-color: #002b49;
  animation: subtle-move 2s infinite;
}

#request-service:hover {
  cursor: pointer;
  animation: shadow 0.5s forwards;
}

@keyframes shadow {
  from {
    box-shadow: 0px 0px 0px 0px #002b49;
  }
  to {
    box-shadow: 0px 0px 1px 1px #002b49;
  }
}

@keyframes subtle-move {
  0% {
    transform: translateX(0px);
  }
  50% {
    transform: translateX(3px);
  }
  100% {
    transform: translateX(0px);
  }
}

#about-header {
  text-align: center;
  margin: 0 auto;
  margin-top: 40%;
  margin-bottom: 20%;
  width: 50%;
  color: white;
  font-size: 1rem;
}

#content {
  width: 100%;
  background: linear-gradient(180deg, #ffffff 0%, #ffffff 50%, #fafafa 100%);
  position: relative;
  overflow: hidden;
  z-index: 9;
}

#circular-wrapper {
  position: relative;
  width: 200px;
  height: 200px;
  margin: 0 auto;
  margin-top: 10%;
  z-index: 9;
}

#circular-1 {
  width: 100%;
  position: absolute;
  top: 0;
  left: 0;
}

#circular-2 {
  transition: top 0.02s linear;
  -moz-transition: -moz-transform 0.02s linear;
  -ms-transition: -ms-transform 0.02s linear;
  -webkit-transition: -webkit-transform 0.02s linear;
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
  opacity: 0.8;
}

.blocks {
  display: flex;
  flex-direction: row;
  width: 100%;
  margin-top: 5%;
}

.show {
}

.hide {
  display: none;
}

.thirty {
  width: 30%;
}

.fifty {
  width: 50%;
}

.block {
  margin: 0% 7% 5% 7%;
  display: block;
  text-align: left;
  color: #002b49;
  position: relative;
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
}
</style>
