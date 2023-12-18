<template>
  <div id="app">
    <div id="top"></div>
    <div id="header">
      <img :src="require('./assets/Coffee Syndicate Logo Full.svg')" alt="Coffee Syndicate Logo" id="logo" @click="scrollTo('#top')">
    </div>
    <img src="./assets/bottom_water.svg" alt="water" id="water" :style="{left: waterLeft + 'px'}">

    <div id="content">
      <img :src="require('./assets/Coffee Syndicate Mark.svg')" alt="Coffee Syndicate Mark" id="mark" @click="scrollTo('#top')">
      <div id="scroll-progress-container" :style="{height: position[1] +'px'}"></div>
      <div id="scroll-progress-fill"></div>
      <div class="block" id="about">
        <h1>ABOUT</h1>
        <p>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Quasi voluptatibus facilis vel ullam, voluptate cumque aspernatur ab sapiente debitis officia temporibus, eius vitae non nisi maxime atque. Inventore, ipsam cumque. Lorem ipsum dolor sit amet consectetur adipisicing elit. Quidem, officiis repudiandae dolorem odit voluptatum qui! Dignissimos culpa atque eaque temporibus, excepturi voluptatem facere maiores et corporis harum qui aspernatur similique! Lorem ipsum dolor sit amet consectetur adipisicing elit. Harum expedita natus culpa impedit autem, omnis sapiente exercitationem officia rerum quia consectetur facere saepe voluptate quibusdam nobis eius inventore animi ut. Lorem ipsum dolor sit a
        </p>
      </div>
      <div class="block" id="equipment">
        <h1>EQUIPMENT</h1>
        <p>
          Lorem ipsum, dolor sit amet consectetur adipisicing elit. Cum unde maxime et laborum qui, sapiente, veritatis dolorem ex ab in provident commodi non odio fugit corrupti quae voluptate, neque mollitia!
          <br>
          <br>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Reiciendis blanditiis repudiandae mollitia exercitationem culpa accusamus iste, omnis voluptas at quaerat libero? Nam perspiciatis deserunt, veritatis commodi sequi quas laboriosam reprehenderit.
        </p>
      </div>
      <div class="block" id="service">
        <h1>SERVICE</h1>
        <p>
          Lorem ipsum, dolor sit amet consectetur adipisicing elit. Cum unde maxime et laborum qui, sapiente, veritatis dolorem ex ab in provident commodi non odio fugit corrupti quae voluptate, neque mollitia!
          <br>
          <br>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Reiciendis blanditiis repudiandae mollitia exercitationem culpa accusamus iste, omnis voluptas at quaerat libero? Nam perspiciatis deserunt, veritatis commodi sequi quas laboriosam reprehenderit.
        </p>
      </div>
      <div class="block" id="software">
        <h1>SOFTWARE</h1>
        <p>
          Lorem ipsum, dolor sit amet consectetur adipisicing elit. Cum unde maxime et laborum qui, sapiente, veritatis dolorem ex ab in provident commodi non odio fugit corrupti quae voluptate, neque mollitia!
          <br>
          <br>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Reiciendis blanditiis repudiandae mollitia exercitationem culpa accusamus iste, omnis voluptas at quaerat libero? Nam perspiciatis deserunt, veritatis commodi sequi quas laboriosam reprehenderit.
          <br>
          <br>
          Lorem ipsum dolor sit, amet consectetur adipisicing elit. Optio minima provident architecto, dolorum autem modi culpa ratione, iste perferendis suscipit voluptatum quas harum voluptas ab numquam nostrum rerum, sapiente reiciendis! Lorem ipsum, dolor sit amet consectetur adipisicing elit. Neque saepe vitae mollitia culpa nihil, id ex praesentium, dicta ipsum ratione odit tempora adipisci nam, quis repudiandae repellat reprehenderit fuga repellendus!

        </p>
      </div>
      <div class="block" id="contact">
        <h1>CONTACT</h1>
        <p>
          If you need service, are interested in talking equipment packages or would like to know more about the custom software solutions we've developed for small businesses, please contact us using this form. All inquiries will receive response within a business day.
        </p>
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
  mounted() {},
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
  top: 15px;
  left: 15px;
  z-index: 100;
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
}

.block p {
  width: 50%;
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

</style>
