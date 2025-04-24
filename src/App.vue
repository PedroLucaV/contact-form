<script setup>
  import { ref } from 'vue';
  const formSubmitted = ref(false);
  const selectedQr = ref(null);
  const firstName = ref(null);
  const lastName = ref(null);
  const emailAdress = ref(null);
  const message = ref(null);
  const checkBox = ref(null);
  const regex = /^((?!\.)[\w-_.]*[^.])(@\w+)(\.\w+(\.\w+)?[^.\W])$/gim;
  const finished = ref(false)

  const checkForm = () => {
    formSubmitted.value = true;
    if(firstName.value && lastName.value && emailAdress.value && selectedQr.value && message.value && checkBox.value){
      finished.value = true
    }
    
  }
</script>

<template>
  <div v-if="finished" class="finishedBox">
    <p class="heading"><img src="./assets/images/icon-success-check.svg" alt=""> Message Sent!</p>
    <p>Thanks for completing the form. We'll be in touch soon!</p>
  </div>
  <main>
    <form @submit.prevent="checkForm">
    <h1>Contact Us</h1>
    <div class="components">
      <div class="doubleInp">
        <div class="inpC" :class="{'error-box': formSubmitted && !firstName}">
          <label for="fM">First Name <span class="ast">*</span></label>
          <input v-model="firstName" class="fM" type="text">
          <span class="error" v-if="formSubmitted && !firstName">This field is required</span>
        </div>
        <div class="inpC" :class="{'error-box': formSubmitted && !lastName}">
          <label for="lM">Last Name <span class="ast">*</span></label>
          <input v-model="lastName" type="text" id="lM">
          <span class="error" v-if="formSubmitted && !lastName">This field is required</span>
        </div>
      </div>
      <div class="inpC" :class="{'error-box': formSubmitted && !emailAdress}">
        <label for="emA">Email Adress <span class="ast">*</span></label>
        <input v-model="emailAdress" type="email" id="emA">
        <span class="error" v-if="formSubmitted && !emailAdress || formSubmitted && !emailAdress.match(regex)">Please enter a valid email adress</span>
      </div>
      <div class="inpC">
        <p>Query Type <span class="ast">*</span></p>
        <div class="doubleInp qrS">
          <label for="qr1" class="qr" :class="{active: selectedQr === 'qr1'}"> <!-- Verifica se o qr selecionado é qr1 para receber a classe active-->
              <input type="radio" name="qr" class="qrA" id="qr1" value="qr1" v-model="selectedQr">General Enquiry <!-- Define o valor do radio e o modelo que irá manipular-->
          </label>
          <label for="qr2" class="qr" :class="{active: selectedQr === 'qr2'}">
              <input type="radio" name="qr" class="qrA" id="qr2" value="qr2" v-model="selectedQr">Support Request
          </label>
        </div>
          <span class="error" v-if="formSubmitted && !selectedQr">This field is required</span>
      </div>
      <div class="inpC" :class="{'error-box': formSubmitted && !message}">
        <label for="">Message <span class="ast">*</span></label>
        <textarea v-model="message" type="" class="messBox"></textarea>
        <span class="error" v-if="formSubmitted && !message">This field is required</span>
      </div>
      <div class="checkB">
        <div class="cb">
          <input v-model="checkBox" type="checkbox" name="" class="cbK" id="cbK">
          <label for="cbK">I consent to being contacted by the team <span class="ast">*</span></label>
        </div>
        <span class="error" v-if="formSubmitted && !checkBox">To submit this form, please consent to being contacted</span>
      </div>
      <button type="submit" class="btn">Submit</button>
    </div>
  </form>
  </main>
</template>

<style>

.finishedBox{
  position: absolute;
  background-color: hsl(169, 94%, 12%);
  top: 45px;
  left: calc(50vw - 216.5px);
  height: fit-content;
  display: flex;
  flex-direction: column;
  border-radius: 10px;
  gap: 0.5rem;
  text-align: left;
  color: white;
  padding: 1.5rem;
  width: fit-content;
}

.finishedBox>.heading{
  font-weight: 700;
  font-size: 20px;
  display: flex;
  align-items: center;
  gap: 0.7rem;
}
main{
  width: 1440px;
  display: flex;
  height: 100%;
  align-items: center;
  justify-content: center;
}
 form{
  display: flex;
  gap: 1.5rem;
  font-size: 15px;
  flex-direction: column;
  background-color: white;
  padding: 1.5rem 2rem;
  width: 650px;
  transition: 1s ease;
  height: fit-content;
 }

 form>h1{
  font-size: 30pt;
 }
 input[type=text], .qr, input[type=email]{
  height: 60px;
  width: 100%;
  border: 1px solid hsl(186, 15%, 59%);
  border-radius: 10px;
  padding: 0.5rem 1rem;
  font-size: 18px;
  transition: 0.05s ease;
 }

  input[type=text]:hover, .qr:hover, input[type=email]:hover{
  cursor: pointer;
  border: 2px solid hsl(169, 82%, 27%);
 }

 .cb{
  margin: 0.2rem 0;
  display: flex;
  align-items: center;
  gap: 0.8rem;
 }

 .checkB{
  display: flex;
  flex-direction: column;
  gap: 0.2rem;
 }

 .error{
  color: hsl(0, 66%, 54%);
  margin-top: 0.1rem;
 }

 .error-box>input{
  border: 1px hsl(0, 66%, 54%) solid;
 }

.cbK:checked {
  background-color: hsl(169, 82%, 27%);
  border-color: hsl(169, 82%, 27%);
}

.ast{
  color: hsl(169, 82%, 27%);
 }

 .qr.active {
  background-color: hsl(148, 38%, 91%);
  border: 2px solid hsl(169, 82%, 27%);
}

 .components{
  display: flex;
  flex-direction: column;
  gap: 1rem;
  width: 100%;
 }

 .doubleInp{
  display: flex;
  width: 100%;
  justify-content: space-between;
 }

 .qrS>.qr{
  width: 49%;
  display: flex;
  align-items: center;
  padding-left: 1.5rem;
  position: relative;
  gap: 1rem;
  font-size: 18px;
 }

 .qr>input{
  height: 20px;
  width: 20px;
 }

 .inpC{
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
 }

 .doubleInp>.inpC{
  width: 49%;
 }

 .messBox{
  height: 100px !important;
  font-size: 12pt;
  max-width: 100%;
  min-width: 100%;
  min-height: 100px;
  resize: none;
  padding: 1rem;
  text-wrap: wrap;
 }

 .btn{
  height: 50px;
  background-color: hsl(169, 82%, 27%);
  color: white;
  font-weight: 700;
  border: none;
  font-size: 11pt;
  border-radius: 10px;
 }
</style>