<template>
  <div class="form">
    <div class="form-block">
      <div class="field-block half">
        <label for="name">Name</label>
        <input required type="text" id="name" />
      </div>
      <div class="field-block half">
        <label for="business">Business Name</label>
        <input type="text" id="business" />
      </div>
    </div>
    <div class="form-block">
      <div class="field-block half">
        <label for="email">Email</label>
        <input type="email" id="email" />
      </div>
      <div class="field-block half">
        <label for="phone">Phone</label>
        <input type="tel" id="phone" />
      </div>
    </div>
    <div class="form-block">
      <div class="field-block half">
        <label for="service">How can we help?</label>
        <select id="service">
          <option value="1">Service 1</option>
          <option value="2">Service 2</option>
          <option value="3">Service 3</option>
        </select>
      </div>
    </div>
    <div class="form-block">
      <div class="field-block full">
        <label for="message">Message</label>
        <textarea rows="10" id="message"></textarea>
      </div>
    </div>
    <div class="form-block">
      <div class="field-block quarter">
        <button>Submit</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'FormComponent',
}
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
}

input:disabled {
  background-color: #fff;
  color: #002b49;
  border: 1px solid #002b49;
  cursor: not-allowed;
}

textarea:disabled {
  background-color: #fff;
  color: #002b49;
  border: 1px solid #002b49;
  cursor: not-allowed;
}

select:disabled {
  background-color: #fff;
  color: #002b49;
  border: 1px solid #002b49;
  cursor: not-allowed;
}

</style>
