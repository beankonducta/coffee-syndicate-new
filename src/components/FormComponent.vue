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
        <input type="tel" id="phone" :value="formattedPhone" @input="formatPhoneNumber($event)" />
      </div>
    </div>
    <div class="form-block" v-if="!submitted">
      <div class="field-block half">
        <label for="service">How can we help?</label>
        <div class="custom-select" @click="toggleDropdown('service')">
          <div class="selected">{{ getServiceLabel }}</div>
          <div class="dropdown" v-if="activeDropdown === 'service'">
            <div class="option" @click="service = '1'">Equipment Purchase</div>
            <div class="option" @click="service = '2'">Service / Maintenance</div>
            <div class="option" @click="service = '4'">Other</div>
          </div>
        </div>
      </div>
      <div class="field-block half" v-if="service == 1">
        <label for="type">Type</label>
        <div class="custom-select" @click="toggleDropdown('type')">
          <div class="selected">{{ getTypeLabel }}</div>
          <div class="dropdown" v-if="activeDropdown === 'type'">
            <div class="option" @click="type = 'New'">New</div>
            <div class="option" @click="type = 'Used'">Used</div>
          </div>
        </div>
      </div>
      <div class="field-block half" v-if="service == 2">
        <label for="type">Type</label>
        <div class="custom-select" @click="toggleDropdown('equipType')">
          <div class="selected">{{ getEquipTypeLabel }}</div>
          <div class="dropdown" v-if="activeDropdown === 'equipType'">
            <div class="option" @click="equipType = 'Espresso machine'">Espresso machine</div>
            <div class="option" @click="equipType = 'Grinder'">Grinder</div>
            <div class="option" @click="equipType = 'Brewer'">Brewer</div>
            <div class="option" @click="equipType = 'Coffee roaster'">Coffee roaster</div>
            <div class="option" @click="equipType = 'Other'">Other</div>
          </div>
        </div>
      </div>
    </div>
    <div class="form-block" v-if="!submitted">
      <div class="field-block half" v-if="service == 1">
        <label for="equipment">What equipment?</label>
        <div class="custom-select" @click="toggleDropdown('equipment')" :class="{ disabled: type === '' }">
          <div class="selected">{{ getEquipmentLabel }}</div>
          <div class="dropdown" v-if="activeDropdown === 'equipment' && type !== ''">
            <div class="option" @click="equipment = 'Espresso machine'">Espresso machine</div>
            <div class="option" @click="equipment = 'Grinder'">Grinder</div>
            <div class="option" @click="equipment = 'Brewer'">Brewer</div>
            <div class="option" @click="equipment = 'Full package'">Full package</div>
            <div class="option" @click="equipment = 'Other'">Other</div>
          </div>
        </div>
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
      activeDropdown: null,
    };
  },
  methods: {
    formatPhoneNumber(event) {
      // Remove all non-numeric characters
      let cleaned = event.target.value.replace(/\D/g, '');
      
      // Trim to 10 digits
      cleaned = cleaned.substring(0, 10);
      
      // Add dots if we have enough numbers
      let formatted = cleaned;
      if (cleaned.length >= 4) {
        formatted = cleaned.slice(0, 3) + '.' + cleaned.slice(3);
      }
      if (cleaned.length >= 7) {
        formatted = formatted.slice(0, 7) + '.' + formatted.slice(7);
      }
      
      this.phone = cleaned; // Store raw number for validation
      event.target.value = formatted; // Display formatted number
    },
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
            message: data,
          },
          "ypG0JnGXYmHsx5aIm"
        ).then((response) => {
          console.log('SUCCESS!', response.status, response.text);
        }, (error) => {
          console.log('FAILED...', error);
        });
        this.submitted = true;
      } catch (error) {
        console.log({ error });
        return;
      }
    },
    toggleDropdown(dropdown) {
      this.activeDropdown = this.activeDropdown === dropdown ? null : dropdown;
    },
  },
  computed: {
    validEmail() {
      const regex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      return regex.test(this.email);
    },
    validPhone() {
      return this.phone.length === 10;
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
    formattedPhone() {
      // Format the stored phone number for display
      if (!this.phone) return '';
      
      let formatted = this.phone;
      if (this.phone.length >= 4) {
        formatted = formatted.slice(0, 3) + '.' + formatted.slice(3);
      }
      if (this.phone.length >= 7) {
        formatted = formatted.slice(0, 7) + '.' + formatted.slice(7);
      }
      return formatted;
    },
    getServiceLabel() {
      const options = {
        '1': 'Equipment Purchase',
        '2': 'Service / Maintenance',
        '4': 'Other'
      };
      return options[this.service] || 'Select an option';
    },
    getTypeLabel() {
      return this.type || 'Select type';
    },
    getEquipTypeLabel() {
      return this.equipType || 'Select equipment type';
    },
    getEquipmentLabel() {
      return this.equipment || 'Select equipment';
    },
  },
  mounted() {
    // Close dropdown when clicking outside
    document.addEventListener('click', (e) => {
      if (!e.target.closest('.custom-select')) {
        this.activeDropdown = null;
      }
    });
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
  transition: opacity 0.3s ease, transform 0.3s ease;
  position: relative;
  z-index: 1;
}

.form-block:hover {
  z-index: 2;
}

.field-block {
  display: flex;
  flex-direction: column;
  width: 100%;
  margin-right: 10px;
  margin-bottom: 20px;
  transition: transform 0.3s ease;
}

.field-block:hover:not(:has(button:disabled)) {
  transform: translateY(-2px);
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
  margin-bottom: 8px;
  font-family: "Prompt", sans-serif;
  color: #002b49;
  transition: color 0.3s ease;
}

.field-block:hover label {
  color: #004d80;
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
  transition: all 0.3s ease;
  box-shadow: 0 2px 4px rgba(0, 43, 73, 0.1);
}

input:focus,
textarea:focus,
select:focus {
  border: 1px solid #002b49;
  outline: none;
  transform: translateY(-2px);
  box-shadow: 0 4px 8px rgba(0, 43, 73, 0.2);
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
  animation: fadeInUp 0.5s ease forwards;
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

button {
  background-color: #002b49;
  color: #fff;
  border: 1px solid #002b49;
  border-radius: 5px;
  padding: 10px 20px;
  font-size: 1rem;
  font-family: "Prompt", sans-serif;
  cursor: pointer;
  transition: all 0.3s ease;
}

button:hover:not(:disabled) {
  background-color: #fff;
  color: #002b49;
  border: 1px solid #002b49;
  transform: translateY(-2px);
  box-shadow: 0 4px 8px rgba(0, 43, 73, 0.2);
}

button:disabled {
  background-color: #f5f5f5;
  color: #002b49;
  border: 1px solid #002b49;
  opacity: 0.5;
  cursor: not-allowed;
  transform: none !important;
  box-shadow: none !important;
  transition: none !important;
}

button:disabled:hover {
  transform: none !important;
  transition: none !important;
  box-shadow: none !important;
  background-color: #f5f5f5 !important;
  color: #002b49 !important;
  border: 1px solid #002b49 !important;
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

.field-block:has(input:disabled),
.field-block:has(select:disabled),
.field-block:has(textarea:disabled) {
  transform: none !important;
  transition: none !important;
  opacity: 0.5;
}

.field-block:has(input:disabled):hover,
.field-block:has(select:disabled):hover,
.field-block:has(textarea:disabled):hover {
  transform: none !important;
}

.field-block:has(input:disabled) label,
.field-block:has(select:disabled) label,
.field-block:has(textarea:disabled) label {
  color: #002b49;
  opacity: 0.5;
  transition: none;
}

.field-block:has(button:disabled) {
  transform: none !important;
  transition: none !important;
}

.field-block:has(button:disabled):hover {
  transform: none !important;
}

.custom-select {
  position: relative;
  width: 100%;
  cursor: pointer;
  z-index: 1;
}

.custom-select.active {
  z-index: 3;
}

.selected {
  border: 1px solid #002b49;
  border-radius: 5px;
  padding: 10px;
  font-size: 1rem;
  font-family: "Prompt", sans-serif;
  color: #002b49;
  background: white;
  transition: all 0.3s ease;
  box-shadow: 0 2px 4px rgba(0, 43, 73, 0.1);
  position: relative;
}

.selected::after {
  content: '▼';
  position: absolute;
  right: 10px;
  top: 50%;
  transform: translateY(-50%);
  font-size: 0.8rem;
}

.dropdown {
  position: absolute;
  top: 100%;
  left: 0;
  right: 0;
  background: white;
  border: 1px solid #002b49;
  border-radius: 5px;
  margin-top: 5px;
  box-shadow: 0 4px 8px rgba(0, 43, 73, 0.2);
  z-index: 4;
  max-height: 200px;
  overflow-y: auto;
  animation: dropdownFade 0.2s ease;
}

@keyframes dropdownFade {
  from {
    opacity: 0;
    transform: translateY(-10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.option {
  padding: 10px;
  transition: all 0.2s ease;
}

.option:hover {
  background-color: rgba(0, 43, 73, 0.1);
}

.custom-select:focus-within .selected {
  border-color: #004d80;
  box-shadow: 0 4px 8px rgba(0, 43, 73, 0.2);
}

.custom-select.disabled {
  opacity: 0.5;
  cursor: not-allowed;
}

.custom-select.disabled .selected {
  background-color: #f5f5f5;
}

.custom-select.disabled:hover .selected {
  transform: none;
  box-shadow: 0 2px 4px rgba(0, 43, 73, 0.1);
}

.dropdown::before {
  content: '';
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: -1;
  pointer-events: none;
}

</style>
