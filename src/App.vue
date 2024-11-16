<template>
  <div id="app" @mousemove="handleMouseMove">
    <div class="header-link" @click="scrollTo('#contact')">REQUEST SERVICE</div>
    <div id="top"></div>
    <div id="header">
      <div class="dot-pattern"></div>
      <img
        :class="position[1] > 500 ? 'hide' : ''"
        :src="require('./assets/Coffee Syndicate Logo Full.svg')"
        alt="Coffee Syndicate Logo"
        id="logo"
      />
      <div class="wave-container">
        <svg data-name="Layer 1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1200 120" preserveAspectRatio="none">
          <path d="M321.39,56.44c58-10.79,114.16-30.13,172-41.86,82.39-16.72,168.19-17.73,250.45-.39C823.78,31,906.67,72,985.66,92.83c70.05,18.48,146.53,26.09,214.34,3V0H0V27.35A600.21,600.21,0,0,0,321.39,56.44Z" class="shape-fill"></path>
        </svg>
      </div>
    </div>
    <!-- <img
      src="./assets/bottom_water.svg"
      alt="water"
      id="water"
      :style="{ marginLeft: `calc(-90% + ${waterLeft}px)` }"
    /> -->
    <div
      id="tooltip"
      :style="{ top: `${mousePos.y}px`, left: `${mousePos.x}px` }"
      v-if="toolTip.show"
    >
      <p>{{ toolTip.text }}</p>
    </div>
    <div id="content">
      <img
        :class="position[1] < 350 ? 'hide no-mobile' : 'no-mobile'"
        :src="require('./assets/Coffee Syndicate Mark.svg')"
        alt="Coffee Syndicate Mark"
        id="mark"
        @click="scrollTo('#top')"
      />
      <div
        id="scroll-progress-container"
        :style="{ height: scrollBarHeight }"
        class="no-mobile"
      ></div>
      <div id="scroll-progress-fill no-mobile"></div>
      <div class="block" id="about" ref="aboutBlock">
        <div class="inner-block-full">
          <h1 ref="about" id="about-header">ABOUT</h1>
          <p>
            Coffee Syndicate, based in Salt Lake City, specializes in coffee
            equipment sales and services. Since 2017, we have been working on
            equipment and are trained and certified by the manufacturers we
            represent.
            <br />
            <br />
            We offer a variety of equipment packages tailored to your needs and
            budget, scheduled preventative maintenance plans to ensure your
            equipment operates smoothly, and comprehensive rebuilds and repairs.
          </p>
          <div class="spacer"></div>
        </div>
      </div>
      <div class="block" id="equipment" ref="equipmentBlock">
        <div class="inner-block">
          <h1 ref="equipment" id="equipment-header">EQUIPMENT</h1>
          <h2>ESPRESSO MACHINES, GRINDERS & BREWERS</h2>
          <p>
            Explore our selection of espresso machines, grinders, and brewers
            from renowned brands such as <a v-for="brand of brands" :key="brand.name" :href="brand.href" target="_blank">{{ brand.name }}, </a> and more. Enjoy free delivery from
            our warehouse and complimentary installation with our full equipment
            packages.
            <br /><br />
            Additionally, we offer fully rebuilt and cleaned used equipment,
            complete with an in-house warranty on parts and labor.
          </p>
          <h2>WATER FILTRATION</h2>
          <p>
            Water filtration is an essential aspect of any coffee equipment
            setup. We provide a range of water filtration solutions designed to
            accommodate your needs.
          </p>
          <div class="spacer"></div>
        </div>
        <div class="inner-block">
          <!-- <div id="spro-container"> -->
          <img src="./assets/sean_ora.png" alt="Spro" id="spro" />
          <!-- <img
              src="./assets/Equipment-01.svg"
              alt="Espresso Machine"
              id="e65"
            />
            <img src="./assets/Equipment-05.svg" alt="Gauge" id="gauge" /> -->
          <!-- </div> -->
        </div>
      </div>
      <div class="block" id="service" ref="serviceBlock">
        <div class="inner-block">
          <h1 ref="service" id="service-header">SERVICE</h1>
          <h2>PREVENTATIVE PLANS</h2>
          <div id="three-six-twelve">
            <img
              src="./assets/Equipment-02.svg"
              alt="3"
              class="calendar bounce-1"
              @mouseenter="show(3)"
              @mouseleave="hide()"
            />
            <img
              src="./assets/Equipment-03.svg"
              alt="6"
              class="calendar bounce-2"
              @mouseenter="show(6)"
              @mouseleave="hide()"
            />
            <img
              src="./assets/Equipment-04.svg"
              alt="12"
              class="calendar bounce-3"
              @mouseenter="show(12)"
              @mouseleave="hide()"
            />
          </div>
          <p>
            Preventative maintenance is the most effective way to keep your
            equipment in optimal condition. We provide 3, 6, and 12-month plans,
            which will prolong the lifespan of your equipment.
          </p>
          <h2>REPAIRS</h2>
          <p>
            If issues arise with your coffee equipment, we are available during
            regular business hours to get you back up and running. We also offer
            emergency service outside of regular hours and on weekends in case
            of urgent situations.
          </p>
          <h2>REBUILDS</h2>
          <p>
            If your equipment is in need of a full rebuild we're more than happy
            to help. We have extensive experience in rebuilding espresso machines,
            grinders, coffee roasters, drip brewers, and other coffee machines.
            All rebuilds come with our in-house warranty.
          </p>
          <div class="spacer"></div>
        </div>
        <div class="inner-block">
          <div id="repair-container">
            <img src="./assets/repair.png" alt="Repair" id="repair" />
            <div id="wrench-container" class="no-mobile">
              <img
                src="./assets/wrench-01.svg"
                alt="Wrench"
                class="icon"
                id="wrench"
              />
              <img
                src="./assets/wrench-03.svg"
                alt="Bolt"
                class="icon"
                id="bolt"
              />
              <img
                src="./assets/wrench-02.svg"
                alt="Working"
                class="icon"
                id="working"
              />
            </div>
          </div>
        </div>
      </div>
      <div class="block" id="contact" ref="contactBlock">
        <div class="inner-block-form">
          <h1 ref="contact" id="contact-header">CONTACT</h1>
          <p>
            If you need service or are interested in talking equipment packages, please contact us using this form.
            All inquiries will receive response within a business day.
          </p>
          <FormComponent />
        </div>
      </div>
    </div>
    <div id="footer">
      <div class="footer-wave-container">
        <svg data-name="Layer 1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1200 120" preserveAspectRatio="none">
          <path d="M321.39,56.44c58-10.79,114.16-30.13,172-41.86,82.39-16.72,168.19-17.73,250.45-.39C823.78,31,906.67,72,985.66,92.83c70.05,18.48,146.53,26.09,214.34,3V0H0V27.35A600.21,600.21,0,0,0,321.39,56.44Z" class="shape-fill"></path>
        </svg>
      </div>
      <p>© {{ currentYear }} Coffee Syndicate</p>
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
    document.fonts.ready.then(() => {
      this.$el.classList.add('fonts-loaded');
    });

    const rows = 5;
    const cols = 24;
    this.binary = new Array(rows)
      .fill(null)
      .map(() =>
        new Array(cols).fill(null).map(() => Math.round(Math.random()))
      );
    setInterval(() => {
      for (let l = 0; l < rows; l++) {
        this.binary[l].unshift(this.binary[l].pop());
      }
    }, 500);
    this.observeHeader();
    this.animateWater();
    this.observeBlocks();
  },
  computed: {
    height() {
      return document.documentElement.clientHeight;
    },
    currentYear() {
      return new Date().getFullYear();
    },
    scrollBarHeight() {
      return (
        (this.position[1] /
          (document.documentElement.scrollHeight - this.height)) *
          100 +
        "%"
      );
    },
  },
  data() {
    return {
      waterLeft: 0,
      targetWaterLeft: 0,
      binary: [],
      showVal: 0,
      mousePos: {
        x: 0,
        y: 0,
      },
      toolTip: {
        show: false,
        text: "",
      },
      aboutHeader: false,
      equipmentHeader: false,
      serviceHeader: false,
      softwareHeader: false,
      contactHeader: false,
      brands: [
        {name: "La Marzocco", href: "https://www.lamarzoccousa.com/"},
        {name: "Synesso", href: "https://synesso.com/"},
        {name: "Slayer", href: "https://slayerespresso.com/"},
        {name: "Mahlkonig", href: "https://www.mahlkoenig.com/"},
        {name: "Compak", href: "https://www.compakgrinders.com/"},
        {name: "Ground Control", href: "https://www.groundcontrol.coffee/"},
        {name: "Fetco", href: "https://www.fetco.com/"},

      ]
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
        rootMargin: "0px",
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
    },
    showToolTip(text) {
      this.toolTip = {
        show: true,
        text,
      };
    },
    hideToolTip() {
      this.toolTip = {
        show: false,
        text: "",
      };
    },
    animateWater() {
      const diff = this.targetWaterLeft - this.waterLeft;
      this.waterLeft += diff * 0.05;
      
      if (Math.abs(diff) > 0.01) {
        requestAnimationFrame(this.animateWater);
      }
    },
    observeBlocks() {
      const options = {
        threshold: 0.2,
        rootMargin: "0px"
      };

      const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
          if (entry.isIntersecting) {
            // console.log('Block entering viewport:', entry.target.id);
            entry.target.classList.add('visible');
          }
        });
      }, options);

      // Use nextTick to ensure DOM is ready
      this.$nextTick(() => {
        const blocks = [
          this.$refs.aboutBlock,
          this.$refs.equipmentBlock,
          this.$refs.serviceBlock,
          this.$refs.contactBlock
        ];
        
        // console.log('Found blocks:', blocks.filter(Boolean).length);
        
        blocks.forEach(block => {
          if (block && block instanceof Element) {
            // Remove any existing classes first
            block.classList.remove('visible');
            // Add initial state
            block.style.opacity = '0';
            block.style.transform = 'translateY(20px)';
            try {
              observer.observe(block);
              // console.log('Successfully observing block:', block.id);
            } catch (error) {
              // console.error('Error observing block:', block.id, error);
            }
          }
        });
      });
    },
  },
  watch: {
    position: {
      handler(val) {
        this.targetWaterLeft = val[1] / 4;
        requestAnimationFrame(this.animateWater);
      },
      deep: true
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

/* Hide scrollbar for Chrome, Safari and Opera */
body::-webkit-scrollbar {
  display: none;
}

/* Hide scrollbar for IE, Edge and Firefox */
body {
  -ms-overflow-style: none; /* IE and Edge */
  scrollbar-width: none; /* Firefox */
}

h1,
h2,
h3,
h4,
h5,
h6 {
  font-family: "Manufaktur", sans-serif;
}

a {
  color: #d15e14;
  text-decoration: none;
  position: relative;
  transition: color 0.3s ease;
}

a::after {
  content: '';
  position: absolute;
  width: 100%;
  height: 2px;
  bottom: -2px;
  left: 0;
  background-color: #d15e14;
  transform: scaleX(0);
  transform-origin: right;
  transition: transform 0.3s ease;
}

a:hover {
  color: #002b49;
}

a:hover::after {
  transform: scaleX(1);
  transform-origin: left;
}

p {
  font-size: calc(0.5rem + 0.5vw);
  line-height: 1.5;
  font-family: "Prompt", sans-serif;
  color: #002b49;
}

#footer p {
  color: white;
  font-family: "Manufaktur", sans-serif;
  text-transform: uppercase;
}

#app {
  background: #002b49;
  overflow-x: clip;
  min-height: 80vh;
  transition: filter 1s ease;
  transition: opacity 1s ease-out, transform 1s ease-out;
  opacity: 0;
}

#app.fonts-loaded {
  opacity: 1;
}

#header {
  height: 500px;
  display: flex;
  justify-content: space-between;
  position: relative;
  overflow: visible;
  padding-bottom: 0;
  z-index: 3;
}

/* Create multiple decorative elements */
#header::before {
  content: '';
  position: absolute;
  width: 100%;
  height: 100%;
}

.dot-pattern {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 120%;
  background-image: radial-gradient(rgba(255, 255, 255, 0.1) 1px, transparent 1px);
  background-size: 20px 20px;
  opacity: 0.3;
}

#header #logo {
  height: 300px;
  top: 15px;
  left: calc(50% - 150px);
  transition: all 0.5s ease;
  position: relative;
  z-index: 3;
}

#header #logo:not(.hide) {
  animation: float 6s ease-in-out infinite;
}

@keyframes shimmer {
  0% {
    background-position: 0% 0%;
  }
  100% {
    background-position: 20% 20%;
  }
}

@keyframes float {
  0% {
    transform: translateY(0px);
  }
  50% {
    transform: translateY(-10px);
  }
  100% {
    transform: translateY(0px);
  }
}

#tooltip {
  position: absolute;
  background: #d15e14;
  color: white;
  padding: 10px;
  border-radius: 5px;
  z-index: 1000;
}

.header-link {
  font-family: "Manufaktur", sans-serif;
  font-size: calc(0.5rem + 0.5vw);
  color: white;
  cursor: pointer;
  padding: 12px 24px;
  margin: 20px;
  text-align: center;
  background: #d15e14;
  border-radius: 3px;
  position: fixed;
  top: 0;
  right: 0;
  z-index: 1000;
  letter-spacing: 0.1em;
  border: 2px solid #d15e14;
  animation: pulse 3s infinite;
  transition: all 0.3s ease;
}

.header-link:hover {
  background: transparent;
  color: #d15e14;
  transform: translateY(-2px);
  animation: none;
}

@keyframes pulse {
  0% {
    transform: translateY(0);
    box-shadow: 0 0 0 0 rgba(209, 94, 20, 0.2);
  }
  
  70% {
    transform: translateY(-2px);
    box-shadow: 0 4px 8px rgba(209, 94, 20, 0.2);
  }
  
  100% {
    transform: translateY(0);
    box-shadow: 0 0 0 0 rgba(209, 94, 20, 0);
  }
}

@media screen and (max-width: 1100px) {
  .header-link {
    font-size: calc(0.6rem + 0.5vw);
    padding: 8px 16px;
    margin: 12px;
  }
}

#mark {
  height: 100px;
  position: fixed;
  cursor: pointer;
  top: 15px;
  left: 15px;
  z-index: 100;
  transition: opacity 0.8s ease, filter 0.8s ease, transform 0.8s ease;
}

#mark.hide {
  opacity: 0;
  filter: blur(10px);
  transform: translateY(-20px);
}

#mark:not(.hide) {
  opacity: 1;
  filter: blur(0px);
  transform: translateY(0);
}

#mark:hover {
  scale: .9;
}

#content {
  background-color: #ffffff;
  background-image: url("https://www.transparenttextures.com/patterns/light-wool.png");
  position: relative;
  overflow: hidden;
  z-index: 1;
  margin-top: -70px;
}

.block {
  margin-top: 5%;
  margin-bottom: 5%;
  display: flex;
  opacity: 0;
  transform: translateY(20px);
  transition: opacity 0.8s ease-out, transform 0.8s ease-out;
  will-change: opacity, transform;
}

.block.visible {
  opacity: 1 !important;
  transform: translateY(0) !important;
}

@media only screen and (min-width: 1200px) and (max-width: 1300px) {
  .inner-block-form {
    position: relative;
    width: 50%;
  }
}

@media only screen and (min-width: 1300px) and (max-width: 1500px) {
  .inner-block-form {
    position: relative;
    width: 75%;
  }
}

@media only screen and (min-width: 1400px) {
  .inner-block-form {
    position: relative;
    width: 50%;
  }
}

@media only screen and (max-width: 1200px) {
  .inner-block-form {
    position: relative;
    width: 100%;
  }
}

@media screen and (max-width: 1100px) {
  .block {
    flex-direction: column;
    width: calc(100% - 100px);
    margin-left: 50px;
    text-align: justify;
  }
  .inner-block {
    position: relative;
    width: 100%;
    min-height: 200px;
  }
  .no-mobile {
    display: none;
  }

  .block img {
    width: 80px;
  }
  #header #logo {
    position: absolute;
    z-index: 0;
  }

  .spacer {
    height: 10px;
  }
  #spro {
    margin-top: 5%;
    width: 100%;
    margin-left: 0%;
    border-radius: 5px;
  }
  #software-img {
    width: 100%;
    margin-left: 0%;
    border-radius: 5px;
  }
  #repair {
    width: 100%;
    left: 0%;
    border-radius: 5px;
  }
  .calendar {
    width: 10%;
    padding: 0px;
  }
  h1 {
    font-size: calc(1.6rem + 1vw);
    color: #d15e14;
  }
  h2 {
    font-size: calc(0.7rem + 1vw);
    color: #d15e14;
    letter-spacing: 0.2em;
  }
  p {
    font-size: calc(0.75rem + 0.5vw);
    line-height: 1.6;
  }
  .header-link {
    font-size: calc(0.75rem + 0.5vw);
  }
}

@media screen and (min-width: 1100px) {
  .block {
    flex-direction: row;
    width: calc(100% - 230px);
    margin-left: 115px;
    text-align: justify;
  }
  .inner-block {
    position: relative;
    width: 50%;
  }
  .spacer {
    height: 100px;
  }
  #header #logo {
    position: absolute;
  }
  #spro {
    margin-top: 5%;
    width: 100%;
    margin-left: 45%;
    border-radius: 5px;
  }
  #software-img {
    width: 100%;
    margin-left: 45%;
    border-radius: 5px;
  }
  #repair {
    width: 100%;
    left: 45%;
    border-radius: 5px;
    position: absolute;
  }
  .calendar {
    width: 15%;
    padding: 20px;
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
  position: relative;
  overflow: visible;
  z-index: 3;
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
  margin-bottom: -10px;
  width: 200%;
}

.icon {
  margin-left: 25%;
  width: 50%;
}

#wrench-container {
  position: absolute;
  top: 35%;
  left: 0%;
  width: 50%;
}

#wrench {
  width: 100%;
  position: absolute;
  top: 0;
  left: 0;
  animation: rotate-45-back 2s ease-in-out infinite;
  z-index: 2;
}

#bolt {
  width: 100%;
  position: absolute;
  top: 0;
  left: 0;
  animation: rotate-45-bolt 2s ease-in-out infinite;
}

#working {
  width: 100%;
  animation: rotate-infinite 10s linear infinite;
}

#spro-container {
  position: absolute;
  top: 25%;
  left: 35%;
  width: 50%;
}

#repair-container {
  height: 100%;
  position: relative;
  margin-top: 5%;
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

#content p {
  z-index: 100;
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
  top: 60%;
  left: 15%;
  z-index: 1;
}

.binary-text {
  font-family: "Prompt", sans-serif;
  font-size: calc(0.8rem + 3%);
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
}

@media (prefers-reduced-motion: reduce) {
  * {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
    scroll-behavior: auto !important;
  }
}

/* Add progress fill animation */
#scroll-progress-fill {
  height: 100%;
  width: 100%;
  background: #d15e14;
  transform-origin: top;
  transition: transform 0.3s ease;
}

h1 {
  position: relative;
  overflow: hidden;
  transform: translateY(20px);
  opacity: 0;
  animation: fadeInUp 0.8s ease forwards;
}

@keyframes fadeInUp {
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.calendar {
  transition: transform 0.3s ease, filter 0.3s ease;
}

.calendar:hover {
  transform: scale(1.1);
  filter: brightness(1.1);
}

.block {
  /* Remove opacity and transform from base class */
  transition: opacity 0.8s ease-out, transform 0.8s ease-out;
  will-change: opacity, transform;
}

.block.visible {
  opacity: 1;
  transform: translateY(0);
}

/* Add new wave-container styles */
.wave-container {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  overflow: hidden;
  line-height: 0;
  z-index: 2;
}

.wave-container svg {
  position: relative;
  display: block;
  width: calc(100% + 1.3px);
  height: 70px;
}

.wave-container .shape-fill {
  fill: #002b49;
}

.footer-wave-container {
  position: absolute;
  bottom: 99px;
  left: 0;
  width: 100%;
  overflow: hidden;
  line-height: 0;
  z-index: 2;
}

.footer-wave-container svg {
  transform: rotate(180deg);
  position: relative;
  display: block;
  width: calc(100% + 1.3px);
  height: 70px;
  z-index: 2;
}

.footer-wave-container .shape-fill {
  fill: #002b49;
}
</style>
