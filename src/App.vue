<template>
  <div id="app">
    <div id="upper">
      <!-- <h1 id="y">{{ position[1] }}</h1> -->
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
      <div class="spacer"></div>
      <!-- <h1 id="about-header" :style="{ opacity: (400 - position[1]) / 400 }">
        Coffee Equipment Sales, Service & Software Solutions
      </h1> -->
      <img
        id="bottom-water"
        src="./assets/bottom_water.svg"
        alt="bottom-water"
        :style="{ marginLeft: waterLeft + 'px' }"
      />
    </div>
    <div id="content">
      <!-- <div id="circular-wrapper" @click="openContact()">
        <img id="circular-1" src="./assets/circular-01.png" />
        <img id="circular-2" src="./assets/circular-02.png" />
      </div> -->
      <div id="blocks">
        <div class="block">
          <h2>Sales</h2>
          <p>
            We distribute coffee equipment from trusted manufactures that we've
            relied on in our own cafes over the years. Not all equipment is
            created equal, and when your business depends on providing quality
            and consistency, day in and day out, we think it's worth springing
            for the good stuff. Every brand we sell is one We believe in and one
            which has great parts availability and service policies.
          </p>
          <p class="reveal">Expertise</p>
        </div>
        <div class="block">
          <h2>Service</h2>
          <p>
            No matter how fancy your coffee equipment is, it will eventually
            need some love, either in the form of on site repairs or
            preventative maintenance to keep it running strong. We offer regular
            service Monday thru Friday and emergency service outside of our
            standard window and on weekends and holidays.
          </p>
          <p class="reveal">Request Service</p>
        </div>
        <div class="block">
          <h2>Software</h2>
          <p>
            Over the years of running coffee shops and roasteries we've
            developed some unique software solutions to make running a small
            business much easier. From till tracking to tip distribution and
            even a full featured roasting software, we've been able to
            streamline mundane tasks and save hours every week. We're always
            looking for new challenges to tackle and would love to hear about
            your business and how we can help.
          </p>
          <p class="reveal">Expertise</p>
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
      this.waterLeft = -window.innerWidth + val[1] / 4;
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

.spacer {
  height: 60vh;
}

#app {
  display: flex;
  flex-direction: column;
  background: #002b49;
  overflow-x: hidden;
}

#upper {
  width: 100%;
  height: 100%;
  background: #002b49;
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
  bottom: 0;
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
  position: fixed;
  width: 500px;
  top: 25px;
  left: calc(50% - 250px);
  filter: invert(1);
  mix-blend-mode: difference;
}

#logo-2 {
  z-index: 8;
  position: fixed;
  width: 500px;
  top: 25px;
  left: calc(50% - 250px);
  filter: invert(1);
  mix-blend-mode: difference;
}

#logo-3 {
  z-index: 11;
  position: fixed;
  width: 500px;
  top: 25px;
  left: calc(50% - 250px);
}

#bottom-water {
  position: relative;
  width: 300%;
  margin-bottom: -3%;
  transition: top 0.02s linear;
  -moz-transition: -moz-transform 0.02s linear;
  -ms-transition: -ms-transform 0.02s linear;
  -webkit-transition: -webkit-transform 0.02s linear;
  z-index: 9;
}

#request-service {
  position: fixed;
  top: -1rem;
  right: 0;
  font-size: 1rem;
  padding: .5rem;
  border-radius: 0px 0px 0px 5px;
  color: white;
  filter: invert(1);
  mix-blend-mode: difference;
  z-index: 10;
  background-color: #002b49;
}

#request-service:hover {
  cursor: pointer;
  animation: shadow .5s forwards;
}

@keyframes shadow {
  from {
    box-shadow: 0px 0px 0px 0px #002b49;
  }
  to {
    box-shadow: 0px 0px 1px 1px #002b49;
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

#blocks {
  display: flex;
  flex-direction: row;
  width: 100%;
  margin-top: 10%;
}

.show {
}

.hide {
  display: none;
}

.block {
  margin: 3%;
  width: 30%;
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
}
</style>
