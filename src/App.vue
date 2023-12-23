<template>
  <div id="app">
    <div id="top"></div>
    <div id="header">
      <img :class="position[1] > 500 ? 'hide' : ''" :src="require('./assets/Coffee Syndicate Logo Full.svg')"
        alt="Coffee Syndicate Logo" id="logo" @click="scrollTo('#top')">
    </div>
    <img src="./assets/bottom_water.svg" alt="water" id="water" :style="{ left: waterLeft + 'px' }">

    <div id="content">
      <img :class="position[1] < 350 ? 'hide' : ''" :src="require('./assets/Coffee Syndicate Mark.svg')"
        alt="Coffee Syndicate Mark" id="mark" @click="scrollTo('#top')">
      <div id="scroll-progress-container" :style="{ height: position[1] * .5 + 'px' }"></div>
      <div id="scroll-progress-fill"></div>
      <div class="block" id="about">
        <div class="inner-block-full">
          <h1>ABOUT</h1>
          <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Quasi voluptatibus facilis vel ullam, voluptate
            cumque
            aspernatur ab sapiente debitis officia temporibus, eius vitae non nisi maxime atque. Inventore, ipsam cumque.
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Quidem, officiis repudiandae dolorem odit voluptatum
            qui! Dignissimos culpa atque eaque temporibus, excepturi voluptatem facere maiores et corporis harum qui
            aspernatur similique! Lorem ipsum dolor sit amet consectetur adipisicing elit. Harum expedita natus culpa
            impedit autem, omnis sapiente exercitationem officia rerum quia consectetur facere saepe voluptate quibusdam
            nobis eius inventore animi ut. Lorem ipsum dolor sit a
          </p>
        </div>
      </div>
      <div class="block" id="equipment">
        <div class="inner-block">
          <h1>EQUIPMENT</h1>
          <p>
            Lorem ipsum, dolor sit amet consectetur adipisicing elit. Cum unde maxime et laborum qui, sapiente, veritatis
            dolorem ex ab in provident commodi non odio fugit corrupti quae voluptate, neque mollitia!
            <br>
            <br>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Reiciendis blanditiis repudiandae mollitia
            exercitationem culpa accusamus iste, omnis voluptas at quaerat libero? Nam perspiciatis deserunt, veritatis
            commodi sequi quas laboriosam reprehenderit.
          </p>
        </div>
        <div class="inner-block">
          <div id="spro-container">
            <img src="./assets/Equipment-01.svg" alt="Espresso Machine" id="e65">
            <img src="./assets/Equipment-05.svg" alt="Gauge" id="gauge">
          </div>
        </div>
      </div>
      <div class="block" id="service">
        <div class="inner-block">
          <h1>SERVICE</h1>
          <p>
            Lorem ipsum, dolor sit amet consectetur adipisicing elit. Cum unde maxime et laborum qui, sapiente, veritatis
            dolorem ex ab in provident commodi non odio fugit corrupti quae voluptate, neque mollitia!
            <br>
            <br>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Reiciendis blanditiis repudiandae mollitia
            exercitationem culpa accusamus iste, omnis voluptas at quaerat libero? Nam perspiciatis deserunt, veritatis
            commodi sequi quas laboriosam reprehenderit.
          </p>
          <div id="three-six-twelve">
            <img src="./assets/Equipment-02.svg" alt="3" class="calendar bounce-1">
            <img src="./assets/Equipment-03.svg" alt="6" class="calendar bounce-2">
            <img src="./assets/Equipment-04.svg" alt="12" class="calendar bounce-3">
          </div>
          <p>
            Lorem ipsum, dolor sit amet consectetur adipisicing elit. Cum unde maxime et laborum qui, sapiente, veritatis
            dolorem ex ab in provident commodi non odio fugit corrupti quae voluptate, neque mollitia!
            <br>
            <br>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Reiciendis blanditiis repudiandae mollitia
            exercitationem culpa accusamus iste, omnis voluptas at quaerat libero? Nam perspiciatis deserunt, veritatis
            commodi sequi quas laboriosam reprehenderit.
          </p>
        </div>
        <div class="inner-block">
          <img src="./assets/wrench-01.svg" alt="Wrench" class="icon" id="wrench">
          <img src="./assets/wrench-03.svg" alt="Bolt" class="icon" id="bolt">
          <img src="./assets/wrench-02.svg" alt="Working" class="icon" id="working">
        </div>
      </div>
      <div class="block" id="software">
        <div class="inner-block">
          <h1>SOFTWARE</h1>
          <p>
            Lorem ipsum, dolor sit amet consectetur adipisicing elit. Cum unde maxime et laborum qui, sapiente, veritatis
            dolorem ex ab in provident commodi non odio fugit corrupti quae voluptate, neque mollitia!
            <br>
            <br>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Reiciendis blanditiis repudiandae mollitia
            exercitationem culpa accusamus iste, omnis voluptas at quaerat libero? Nam perspiciatis deserunt, veritatis
            commodi sequi quas laboriosam reprehenderit.
            <br>
            <br>
            Lorem ipsum dolor sit, amet consectetur adipisicing elit. Optio minima provident architecto, dolorum autem
            modi
            culpa ratione, iste perferendis suscipit voluptatum quas harum voluptas ab numquam nostrum rerum, sapiente
            reiciendis! Lorem ipsum, dolor sit amet consectetur adipisicing elit. Neque saepe vitae mollitia culpa nihil,
            id
            ex praesentium, dicta ipsum ratione odit tempora adipisci nam, quis repudiandae repellat reprehenderit fuga
            repellendus!

          </p>
        </div>
      </div>
      <div class="block" id="contact">
        <div class="inner-block">
          <h1>CONTACT</h1>
          <p>
            If you need service, are interested in talking equipment packages or would like to know more about the custom
            software solutions we've developed for small businesses, please contact us using this form. All inquiries will
            receive response within a business day.
          </p>
        </div>
      </div>
    </div>
    <div id="footer">
      <p>© 2020 Coffee Syndicate</p>
    </div>
  </div>
</template>

<script>
import windowScrollPosition from "./window-scroll-position";

export default {
  mixins: [windowScrollPosition("position")],
  name: "App",
  components: {},
  mounted() { },
  computed: {
    height() {
      return document.documentElement.clientHeight;
    },
  },
  data() {
    return {
      waterLeft: 0,
    };
  },
  methods: {
    // submit() {
    //   try {
    //     emailjs.send(
    //       "service_p8uh0l8",
    //       "template_qjvcvxg",
    //       {
    //         name: this.name,
    //         email: this.email,
    //         message: this.name + "\n" + this.email + "\n\n" + this.address,
    //       },
    //       "oEp3EsbHOxJU0T_V-"
    //     );
    //     this.sent = true;
    //   } catch (error) {
    //     console.log({ error });
    //     return;
    //   }
    //   // Reset form field
    //   this.name = "";
    //   this.email = "";
    //   this.address = "";
    //   this.nameDirty = false;
    //   this.emailDirty = false;
    //   this.addressDirty = false;
    // },
    scrollTo(element) {
      document.querySelector(element).scrollIntoView({
        behavior: "smooth",
      });
    },
  },
  watch: {
    position(val) {
      this.waterLeft = val[1] / 2;
      console.log(val);
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
  font-size: calc(1rem + 1vw);
  color: #002b49;
}

p {
  font-size: calc(0.5rem + .5vw);
  line-height: 1.5;
  font-family: "Prompt", sans-serif;
  color: #002b49;
}

#footer p {
  color: white;
}

#app {
  background: #002b49;
  overflow-x: clip;
  min-height: 80vh;
}

#header {
  height: 400px;
  display: flex;
  justify-content: space-between;
  position: sticky;
  top: 0;
}

.header-link {
  font-size: calc(0.5rem + .5vw);
  color: white;
  cursor: pointer;
  margin: 5px;
  width: 100px;
  text-align: center;
  opacity: 100%;
}

#header #logo {
  height: 300px;
  top: 15px;
  cursor: pointer;
  position: absolute;
  left: calc(50% - 150px);
}

#mark {
  height: 100px;
  position: fixed;
  cursor: pointer;
  top: 15px;
  left: 15px;
  z-index: 100;
}

#header #logo:hover,
#mark:hover {
  opacity: 90%;
}

#content {
  background: white;
  position: relative;
  overflow: hidden;
}

.block {
  width: calc(100% - 230px);
  margin-left: 115px;
  margin-top: 5%;
  margin-bottom: 5%;
  display: flex;
  flex-direction: row;
}

.inner-block {
  position: relative;
  width: 50%;
}

.inner-block-full {
  position: relative;
  width: 100%;
}

.rotate-90 {
  transform: rotate(-90deg);
  margin: 15px;
  margin-top: 10vh;
}

.hide {
  opacity: 0;
}

#footer {
  height: 100px;
  display: flex;
  justify-content: center;
  align-items: center;
}

#scroll-progress-container {
  position: fixed;
  top: 0;
  left: 0;
  width: 20px;
  background: #002b49;
  z-index: 100;
  transition: height 0.5s ease;
}

#water {
  margin-bottom: -100px;
  width: 200%;
}

.icon {
  margin-left: 25%;
  width: 50%;
}

#wrench {
  position: absolute;
  top: 25%;
  left: 0;
  animation: rotate-45-back 2s ease-in-out infinite;
}

#spro-container {
  position: absolute;
  top: 0;
  left: 25%;
  width: 50%;
}

#e65 {
  width: 100%;
}

#gauge {
  position: absolute;
  bottom: 25%;
  left: 12%;
  width: 25%;
  animation: gauge-rotate 5s infinite;
}

@keyframes gauge-rotate {
  0% {
    transform: rotate(0deg);
  }

  10% {
    transform: rotate(10deg);
  }

  20% {
    transform: rotate(5deg);
  }

  30% {
    transform: rotate(15deg);
  }

  40% {
    transform: rotate(5deg);
  }

  50% {
    transform: rotate(-5deg);
  }

  60% {
    transform: rotate(0deg);
  }

  70% {
    transform: rotate(5deg);
  }

  80% {
    transform: rotate(10deg);
  }

  90% {
    transform: rotate(7deg);
  }

  100% {
    transform: rotate(13deg);
  }
}

@keyframes rotate-45-back {
  0% {
    transform: rotate(0deg);
  }

  50% {
    transform: rotate(60deg);
  }

  75% {
    transform: translateX(-50px);
  }

  100% {
    transform: rotate(0deg);
    transform: translateX(0px);
  }
}

@keyframes rotate-45-bolt {
  0% {
    transform: rotate(0deg);
  }

  50% {
    transform: rotate(60deg);
  }

  75% {
    transform: rotate(60deg);
  }

  100% {
    transform: rotate(60deg);
  }
}

#bolt {
  position: absolute;
  top: 25%;
  left: 0;
  animation: rotate-45-bolt 2s ease-in-out infinite;
}

#working {
  position: absolute;
  top: 25%;
  left: 0;
  animation: rotate-infinite 10s linear infinite;
}

#three-six-twelve {
  width: 100%;
  display: flex;
  justify-content: space-between;
}

.calendar {
  width: 25%;
}

.hide {
  display: none;
}

@keyframes rotate-infinite {
  0% {
    transform: rotate(0deg);
  }

  100% {
    transform: rotate(360deg);
  }
}

.bounce-1 {
  animation: bounce-1 2s infinite;
}

.bounce-2 {
  animation: bounce-2 2s infinite;
}

.bounce-3 {
  animation: bounce-3 2s infinite;
}

@keyframes bounce-1 {
  0% {
    transform: translateY(0px);
  }

  30% {
    transform: translateY(-5px);
  }

  100% {
    transform: translateY(0px);
  }
}

@keyframes bounce-2 {
  0% {
    transform: translateY(0px);
  }

  40% {
    transform: translateY(-5px);
  }

  100% {
    transform: translateY(0px);
  }
}

@keyframes bounce-3 {
  0% {
    transform: translateY(0px);
  }

  50% {
    transform: translateY(-5px);
  }

  100% {
    transform: translateY(0px);
  }
}</style>
