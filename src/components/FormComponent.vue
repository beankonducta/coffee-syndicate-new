<template>
  <div class="form">
    <div class="form-block" v-if="!submitted">
      <div class="field-block half">
        <label for="name">Name</label>
        <input required type="text" id="name" v-model="name" />
      </div>
      <div class="field-block half">
        <label for="business">Business Name (optional)</label>
        <input type="text" id="business" />
      </div>
    </div>
    <div class="form-block" v-if="!submitted">
      <div class="field-block half">
        <label for="email">Email</label>
        <input type="email" id="email" v-model="email" />
      </div>
      <div class="field-block half">
        <label for="phone">Phone</label>
        <input type="tel" id="phone" v-model="phone" />
      </div>
    </div>
    <div class="form-block" v-if="!submitted">
      <div class="field-block half">
        <label for="service">How can we help?</label>
        <select id="service" v-model="service">
          <option value="1">Equipment Purchase</option>
          <option value="2">Service / Maintenance</option>
          <option value="3">Software / Website</option>
          <option value="4">Other</option>
        </select>
      </div>
      <div class="field-block half" v-if="service == 1">
        <label for="type">Type</label>
        <select id="type" v-model="type">
          <option value="New">New</option>
          <option value="Used">Used</option>
        </select>
      </div>
      <div class="field-block half" v-if="service == 2">
        <label for="type">Type</label>
        <select id="equip-type" v-model="equipType">
          <option value="Espresso machine">Espresso machine</option>
          <option value="Grinder">Grinder</option>
          <option value="Brewer">Brewer</option>
          <option value="Coffee roaster">Coffee roaster</option>
          <option value="Other">Other</option>
        </select>
      </div>
    </div>
    <div class="form-block" v-if="!submitted">
      <div class="field-block half" v-if="service == 1">
        <label for="equipment">What equipment?</label>
        <select id="equipment" v-model="equipment" :disabled="type == ''">
          <option value="Espresso machine">Espresso machine</option>
          <option value="Grinder">Grinder</option>
          <option value="Brewer">Brewer</option>
          <option value="Full package">Full package</option>
          <option value="Other">Other</option>
        </select>
      </div>
      <div class="field-block half" v-if="service == 1">
        <label for="brands">Brands</label>
        <input
          type="text"
          id="brands"
          v-model="brands"
          :disabled="equipment == ''"
        />
      </div>
      <div class="field-block full" v-if="service == 2">
        <label for="model">Model information</label>
        <input
          type="text"
          id="model"
          v-model="model"
          :disabled="equipType == ''"
        />
      </div>
    </div>
    <div class="form-block" v-if="!submitted">
      <div class="field-block full">
        <label for="message">Message</label>
        <textarea rows="10" id="message" v-model="message"></textarea>
      </div>
    </div>
    <div class="form-block" v-if="!submitted">
      <div class="field-block quarter">
        <button :disabled="submitDisabled" @click="submitForm()">SUBMIT</button>
      </div>
    </div>
    <div class="form-block submitted" v-if="submitted">
      <h2>THANK YOU - WE WILL FOLLOW UP SHORTLY</h2>
    </div>
  </div>
</template>

<script>
import emailjs from "emailjs-com";

export default {
  name: "FormComponent",
  data() {
    return {
      service: 1,
      equipment: "",
      brands: "",
      type: "",
      equipType: "",
      model: "",
      name: "",
      email: "",
      phone: "",
      message: "",
      submitted: false,
    };
  },
  methods: {
    submitForm() {
      try {
        const data = JSON.stringify({
          service: this.service,
          equipment: this.equipment,
          brands: this.brands,
          type: this.type,
          equipType: this.equipType,
          model: this.model,
          name: this.name,
          email: this.email,
          phone: this.phone,
          message: this.message,
        });
        emailjs.send(
          "service_ckmnldo",
          "template_77rlqvc",
          {
            data
          },
          "ypG0JnGXYmHsx5aIm"
        );
        this.submitted = true;
      } catch (error) {
        console.log({ error });
        return;
      }
    },
  },
  computed: {
    validEmail() {
      const regex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      return regex.test(this.email);
    },
    validPhone() {
      const regex = /^(\+\d{1,2}\s)?\(?\d{3}\)?[\s.-]\d{3}[\s.-]\d{4}$/;
      return regex.test(this.phone);
    },
    validName() {
      return this.name.length > 2;
    },
    validMessage() {
      return this.message.length > 10;
    },
    submitDisabled() {
      return (
        !this.validEmail ||
        !this.validPhone ||
        !this.validName ||
        !this.validMessage
      );
    },
  },
};
</script>

<style scoped>
.form {
  display: flex;
  flex-direction: column;
  width: 100%;
  margin-top: 5%;
}

.form-block {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 10px;
}

.field-block {
  display: flex;
  flex-direction: column;
  width: 100%;
  margin-right: 10px;
  margin-bottom: 20px;
}

.third {
  width: 30%;
}

.half {
  width: 45%;
}

.quarter {
  width: 20%;
}

.full {
  width: 100%;
}

label {
  font-size: 1rem;
  font-weight: 600;
  margin-bottom: 5px;
  font-family: "Prompt", sans-serif;
  color: #002b49;
}

input,
textarea,
select {
  border: 1px solid #002b49;
  border-radius: 5px;
  padding: 10px;
  font-size: 1rem;
  font-family: "Prompt", sans-serif;
  color: #002b49;
  background: white;
}

textarea {
  resize: none;
}

input:active {
  border: 1px solid #002b49;
  outline: none;
}

input:focus {
  border: 1px solid #002b49;
  outline: none;
}

textarea:active {
  border: 1px solid #002b49;
  outline: none;
}

textarea:focus {
  border: 1px solid #002b49;
  outline: none;
}

select:active {
  border: 1px solid #002b49;
  outline: none;
}

select:focus {
  border: 1px solid #002b49;
  outline: none;
}

.submitted {
  height: 300px;
  width: 100%;
}

button {
  background-color: #002b49;
  color: #fff;
  border: 1px solid #002b49;
  border-radius: 5px;
  padding: 10px;
  font-size: 1rem;
  font-family: "Prompt", sans-serif;
  cursor: pointer;
}

button:hover {
  background-color: #fff;
  color: #002b49;
  border: 1px solid #002b49;
}

button:active {
  background-color: #fff;
  color: #002b49;
  border: 1px solid #002b49;
}

@media only screen and (max-width: 768px) {
  .form {
    width: 100%;
    margin-left: 0;
  }

  .form-block {
    flex-direction: column;
  }

  .field-block {
    width: 100%;
    margin-right: 0;
  }

  .third,
  .half,
  .quarter,
  .full {
    width: 100%;
  }
}

@media only screen and (max-width: 480px) {
  .form {
    width: 100%;
    margin-left: 0;
  }

  .form-block {
    flex-direction: column;
  }

  .field-block {
    width: 100%;
    margin-right: 0;
  }

  .third,
  .half,
  .quarter,
  .full {
    width: 100%;
  }
}

button:disabled {
  background-color: #fff;
  color: #002b49;
  border: 1px solid #002b49;
  cursor: not-allowed;
  opacity: 0.1;
}

input:disabled {
  background-color: #fff;
  color: #002b49;
  border: 1px solid #002b49;
  opacity: 0.1;
  cursor: not-allowed;
}

textarea:disabled {
  background-color: #fff;
  color: #002b49;
  border: 1px solid #002b49;
  opacity: 0.1;
  cursor: not-allowed;
}

select:disabled {
  background-color: #fff;
  color: #002b49;
  border: 1px solid #002b49;
  opacity: 0.1;
  cursor: not-allowed;
}
</style>
