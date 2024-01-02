<template>
  <div id="app" @mousemove="handleMouseMove">
    <div class="header-link" @click="scrollTo('#contact')">REQUEST SERVICE</div>
    <div id="top"></div>
    <div id="header">
      <img :class="position[1] > 500 ? 'hide' : ''" :src="require('./assets/Coffee Syndicate Logo Full.svg')"
        alt="Coffee Syndicate Logo" id="logo">
    </div>
    <img src="./assets/bottom_water.svg" alt="water" id="water" :style="{ marginLeft: `calc(-100% + ${waterLeft}px)` }">

    <div id="content">
      <img :class="position[1] < 350 ? 'hide' : ''" :src="require('./assets/Coffee Syndicate Mark.svg')"
        alt="Coffee Syndicate Mark" id="mark" @click="scrollTo('#top')">
      <div id="scroll-progress-container" :style="{ height: scrollBarHeight }"></div>
      <div id="scroll-progress-fill"></div>
      <div class="block" id="about">
        <div class="inner-block-full">
          <h1 ref="about" id="about-header">ABOUT</h1>
          <p>
            Coffee Syndicate is a Salt Lake City based coffee equipment sales and service company. We've been working on
            equipment since 2015 and are
            trained and certified by the manufacturers we represent. Additionally, from over a decade of running a coffee
            business, we've developed custom
            software solutions to lessen the amount of mundane tasks and data entry that eat away at the time that should
            be spent growing and nurturing your business.
            <br>
            <br>
            We offer a variety of equipment packages to fit your needs and budget, scheduled preventative maintenance
            plans to keep your equipment running smoothly and
            full rebuilds and repairs when things go wrong. We also develop software and websites to help you run your
            business more efficiently.
          </p>
        </div>
      </div>
      <div class="block" id="equipment">
        <div class="inner-block">
          <h1 ref="equipment" id="equipment-header">EQUIPMENT</h1>
          <p>
            From espresso machines to drip brewers, grinders and beyond, we offer coffee equipment from top brands that
            we've put to the test in our own coffee shops over the years.
          </p>
          <h2>ESPRESSO MACHINES</h2>
          <p>
          </p>
          <h2>GRINDERS</h2>
          <p>
          </p>
          <h2>BREWERS</h2>
          <p>
          </p>
          <h2>ACCESSORIES</h2>
          <p>
          </p>
          <h2>WATER FILTRATION</h2>
          <p>
            Water filtration is a critical component of any coffee equipment setup. We offer a variety of water
            filtration options to fit your volumes.
            <br>
            <br>
            Typically we recommend fairly robust filtration, especially with the hardness of Utah water, but each setup is
            customized based on
            the TDS (total dissolved solids) of your water and the volume of water you're using.
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
          <h1 ref="service" id="service-header">SERVICE</h1>
          <p>
            Using coffee equipment, and espresso machines specifically, is a lot like daily driving a car. No matter how
            nice the build, you're
            going to need repairs along the way. We offer a variety of services to keep your equipment running smoothly
            and minimize downtime.
          </p>
          <h2>PREVENTATIVE PLANS</h2>
          <div id="three-six-twelve">
            <img src="./assets/Equipment-02.svg" alt="3" class="calendar bounce-1" @mouseenter="show(3)"
              @mouseleave="hide()">
            <img src="./assets/Equipment-03.svg" alt="6" class="calendar bounce-2" @mouseenter="show(6)"
              @mouseleave="hide()">
            <img src="./assets/Equipment-04.svg" alt="12" class="calendar bounce-3" @mouseenter="show(12)"
              @mouseleave="hide()">
            <!-- <div class="pm-panel" id="three" v-if="showVal === 3">
              <h2>3 MONTHS</h2>
              <p>Text</p>
            </div>
            <div class="pm-panel" id="six" v-if="showVal === 6">
              <h2>3 MONTHS</h2>
              <p>Text</p>
            </div>
            <div class="pm-panel" id="twelve" v-if="showVal === 12">
              <h2>3 MONTHS</h2>
              <p>Text</p>
            </div> -->
          </div>
          <p>
            Preventative maintainance, akin to getting an oil change in your car, is the best way to keep your equipment
            running well.
            We offer 3, 6 and 12 month plans, which are typically following specific manufacturer recommendation, and
            will extend the working
            life of your equipment.
          </p>
          <h2>REPAIRS</h2>
          <p>
            When things go wrong with your espresso machine, grinder, drip brewer or other coffee equipment, we're
            available during business hours
            to get you back up and running. We also offer emergency service off-hours and on weekends if catastrophe
            strikes.
          </p>
          <h2>REBUILDS</h2>
          <p>
            If your equipment is in need of a full rebuild, we can help. We've rebuilt countless espresso machines,
            grinders, coffee roasters, drip brewers and other
            coffee machines. All rebuilds come with a 90 day warranty on parts and labor.
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
          <h1 ref="software" id="software-header">SOFTWARE</h1>
          <p>
            Over the years we've developed a variety of software solutions to help us run our coffee shops more
            efficiently. Being a small business owner
            means wearing a lot of hats and we've found ways to automate or minimize the amount of boring back office work
            required to keep
            things running.
            <br>
            <br>
            We're also skilled in web development and can put in relatively minimal work to get your website out of
            looking
            like a template and into something that's on brand and stands out from the crowd.
            <br>
            <br>
            Specific applications we've found useful include a tip tracking and distribution app, a highly detailed till
            tracking app to make sure cash sales
            are properly accounted for, custom wholesale ordering portals so you can control every detail of how your
            customers order, pay and receive notifications
            related to fulfillment, as well as a variety of Shopify and Square based services to eliminate the need for
            manual data entry. We have some out of the box
            offerings which can be put into action with minimal customization & we're always excited to come up with
            something fully custom to tackle
            whatever time sink you're dealing with.
          </p>
        </div>
        <div class="inner-block">
          <img src="./assets/software-05.svg" alt="Server" id="server">
          <img src="./assets/software-04.svg" alt="Client" id="client">
          <div id="binary">
            <div class="binary-text">
              <span v-for="(row, index) in binary[0]" :key="index">{{ row }}</span>
            </div>
            <div class="binary-text">
              <span v-for="(row, index) in binary[1]" :key="index">{{ row }}</span>
            </div>
            <div class="binary-text">
              <span v-for="(row, index) in binary[2]" :key="index">{{ row }}</span>
            </div>
          </div>
        </div>
      </div>
      <div class="block" id="contact">
        <div class="inner-block">
          <h1 ref="contact" id="contact-header">CONTACT</h1>
          <p>
            If you need service, are interested in talking equipment packages or would like to know more about the custom
            software solutions we've developed for small businesses, please contact us using this form. All inquiries will
            receive response within a business day.
          </p>
          <FormComponent />
        </div>
        <div class="inner-block">

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
import FormComponent from "./components/FormComponent.vue";

export default {
  mixins: [windowScrollPosition("position")],
  name: "App",
  components: {
    FormComponent,
  },
  mounted() {
    const rows = 3;
    const cols = 24;
    this.binary = new Array(rows).fill(null).map(() => new Array(cols).fill(null).map(() => Math.round(Math.random())));
    setInterval(() => {
      for (let l = 0; l < rows; l++) {
        this.binary[l].unshift(this.binary[l].pop());
      }
    }, 500);
    this.observeHeader();
  },
  computed: {
    height() {
      return document.documentElement.clientHeight;
    },
    scrollBarHeight() {
      return (this.position[1] / (document.documentElement.scrollHeight - this.height)) * 100 + "%";
    },
  },
  data() {
    return {
      waterLeft: 0,
      binary: [],
      showVal: 0,
      mousePos: {
        x: 0,
        y: 0,
      },
      toolTip: {
        show: false,
        text: ""
      },
      aboutHeader: false,
      equipmentHeader: false,
      serviceHeader: false,
      softwareHeader: false,
      contactHeader: false
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
    observeHeader() {
      const options = {
        root: null,
        rootMargin: '0px',
        threshold: 1.0,
      };

      const observer = new IntersectionObserver((entries) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting) {
            if (entry.target.id === "about-header") {
              this.aboutHeader = true;
            } else {
              this.aboutHeader = false;
            }
            if (entry.target.id === "equipment-header") {
              this.equipmentHeader = true;
            } else {
              this.equipmentHeader = false;
            }
            if (entry.target.id === "service-header") {
              this.serviceHeader = true;
            } else {
              this.serviceHeader = false;
            }
            if (entry.target.id === "software-header") {
              this.softwareHeader = true;
            } else {
              this.softwareHeader = false;
            }
            if (entry.target.id === "contact-header") {
              this.contactHeader = true;
            } else {
              this.contactHeader = false;
            }
          }
        });
      }, options);

      observer.observe(this.$refs.about);
      observer.observe(this.$refs.equipment);
      observer.observe(this.$refs.service);
      observer.observe(this.$refs.software);
      observer.observe(this.$refs.contact);
    },
    show(number) {
      this.showVal = number;
    },
    hide() {
      this.showVal = 0;
    },
    scrollTo(element) {
      document.querySelector(element).scrollIntoView({
        behavior: "smooth",
      });
    },
    handleMouseMove(event) {
      this.mousePos = {
        x: event.pageX,
        y: event.pageY,
      };
      console.log(this.mousePos)
    },
    showToolTip(text) {
      this.toolTip = {
        show: true,
        text
      }
    },
    hideToolTip() {
      this.toolTip = {
        show: false,
        text: ""
      }
    }
  },
  watch: {
    position(val) {
      this.waterLeft = val[1] / 4;
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
  color: #d15e14;
}

h2 {
  font-size: calc(0.1rem + 1vw);
  color: #d15e14;
  letter-spacing: 0.2em;
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
  max-width: 200px;
  width: auto;
  text-align: center;
  opacity: 100%;
  font-family: "Prompt", sans-serif;
  background: #002b49;
  border-radius: 5px;
  padding: 5px;
  position: fixed;
  top: 0;
  right: 0;
  z-index: 1000;
}

.header-link:hover {
  background: #d15e14;
}

#header #logo {
  height: 300px;
  top: 15px;
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

#mark:hover {
  opacity: 80%;
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
  left: 10%;
  animation: rotate-45-back 2s ease-in-out infinite;
  z-index: 2;
}

#bolt {
  position: absolute;
  top: 25%;
  left: 10%;
  animation: rotate-45-bolt 2s ease-in-out infinite;
}

#working {
  position: absolute;
  top: 25%;
  left: 10%;
  animation: rotate-infinite 10s linear infinite;
}

#spro-container {
  position: absolute;
  top: 25%;
  left: 35%;
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

.pm-panel {
  position: absolute;
  top: 0px;
  left: 0px;
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

#three-six-twelve {
  width: 100%;
  display: flex;
  justify-content: space-between;
}

.calendar {
  width: 15%;
  padding: 20px;
}

.hide {
  display: none;
}

#client {
  width: 40%;
  position: absolute;
  top: 25%;
  right: 5%;
  z-index: 2;
}

#server {
  width: 40%;
  position: absolute;
  top: 25%;
  left: 15%;
  z-index: 2;
}

#binary {
  width: 60%;
  position: absolute;
  top: 35%;
  left: 25%;
  z-index: 1;
}

.binary-text {
  font-family: "Prompt", sans-serif;
  font-size: 1em;
  color: #d15e14;
  display: flex;
  justify-content: space-between;
  width: 100%;
  transition: all 0.5s ease;
}

.binary-text span {
  display: inline-block;
  -webkit-animation: wave-text 1s ease-in-out infinite;
  animation: wave-text 1s ease-in-out infinite;
}

.binary-text span:nth-of-type(1) {
  -webkit-animation-delay: 0s;
  animation-delay: 0s;
}

.binary-text span:nth-of-type(2) {
  -webkit-animation-delay: 0.1s;
  animation-delay: 0.1s;
}

.binary-text span:nth-of-type(3) {
  -webkit-animation-delay: 0.2s;
  animation-delay: 0.2s;
}

.binary-text span:nth-of-type(4) {
  -webkit-animation-delay: 0.3s;
  animation-delay: 0.3s;
}

.binary-text span:nth-of-type(5) {
  -webkit-animation-delay: 0.4s;
  animation-delay: 0.4s;
}

.binary-text span:nth-of-type(6) {
  -webkit-animation-delay: 0.5s;
  animation-delay: 0.5s;
}

.binary-text span:nth-of-type(7) {
  -webkit-animation-delay: 0.6s;
  animation-delay: 0.6s;
}

.binary-text span:nth-of-type(8) {
  -webkit-animation-delay: 0.7s;
  animation-delay: 0.7s;
}

.binary-text span:nth-of-type(9) {
  -webkit-animation-delay: 0.8s;
  animation-delay: 0.8s;
}

.binary-text span:nth-of-type(10) {
  -webkit-animation-delay: 0.9s;
  animation-delay: 0.9s;
}

.binary-text span:nth-of-type(11) {
  -webkit-animation-delay: 1s;
  animation-delay: 1s;
}

.binary-text span:nth-of-type(12) {
  -webkit-animation-delay: 1.1s;
  animation-delay: 1.1s;
}

.binary-text span:nth-of-type(13) {
  -webkit-animation-delay: 1.2s;
  animation-delay: 1.2s;
}

.binary-text span:nth-of-type(14) {
  -webkit-animation-delay: 1.3s;
  animation-delay: 1.3s;
}

.binary-text span:nth-of-type(15) {
  -webkit-animation-delay: 1.4s;
  animation-delay: 1.4s;
}

.binary-text span:nth-of-type(16) {
  -webkit-animation-delay: 1.5s;
  animation-delay: 1.5s;
}

.binary-text span:nth-of-type(17) {
  -webkit-animation-delay: 1.6s;
  animation-delay: 1.6s;
}

.binary-text span:nth-of-type(18) {
  -webkit-animation-delay: 1.7s;
  animation-delay: 1.7s;
}

.binary-text span:nth-of-type(19) {
  -webkit-animation-delay: 1.8s;
  animation-delay: 1.8s;
}

.binary-text span:nth-of-type(20) {
  -webkit-animation-delay: 1.9s;
  animation-delay: 1.9s;
}

.binary-text span:nth-of-type(21) {
  -webkit-animation-delay: 2s;
  animation-delay: 2s;
}

.binary-text span:nth-of-type(22) {
  -webkit-animation-delay: 2.1s;
  animation-delay: 2.1s;
}

.binary-text span:nth-of-type(23) {
  -webkit-animation-delay: 2.2s;
  animation-delay: 2.2s;
}

.binary-text span:nth-of-type(24) {
  -webkit-animation-delay: 2.3s;
  animation-delay: 2.3s;
}

@-webkit-keyframes wave-text {
  00% {
    transform: translateY(0em);
  }

  60% {
    transform: translateY(-0.6em);
  }

  100% {
    transform: translateY(0em);
  }
}

@keyframes wave-text {
  00% {
    transform: translateY(0em);
  }

  60% {
    transform: translateY(-0.6em);
  }

  100% {
    transform: translateY(0em);
  }
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
