<script setup>

</script>

<template>
  <main>
    <form @submit.prevent="">
    <h1>Contact Us</h1>
    <div class="components">
      <div class="doubleInp">
        <div class="inpC">
          <label for="">First Name <span class="ast">*</span></label>
          <input type="text">
        </div>
        <div class="inpC">
          <label for="">Last Name <span class="ast">*</span></label>
          <input type="text">
        </div>
      </div>
      <div class="inpC">
        <label for="">Email Adress <span class="ast">*</span></label>
        <input type="text">
      </div>
      <div class="inpC">
        <p>Query Type <span class="ast">*</span></p>
        <div class="doubleInp qrS">
          <div class="qr">
            <input type="radio" name="qr" id="qr1">
            <label for="qr1">General Enquiry</label>
          </div>
          <div class="qr">
            <input type="radio" name="qr" id="qr2">
            <label for="qr2">Support Request</label>
          </div>
        </div>
      </div>
      <div class="inpC">
        <label for="">Message <span class="ast">*</span></label>
        <input type="text" class="messBox">
      </div>
      <div class="checkB">
        <div class="cb">
          <input type="checkbox" name="" id="">
          <label for="">I consent to being contacted by the team <span class="ast">*</span></label>
        </div>
      </div>
      <button type="submit" class="btn">Submit</button>
    </div>
  </form>
  </main>
</template>

<style>
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
  width: 600px;
  height: fit-content;
 }

 input[type=text], .qr{
  height: 50px;
  width: 100%;
  border: 1px solid hsl(169, 82%, 27%);
  border-radius: 10px;
 }

 .cb{
  display: flex;
  gap: 1rem;
 }

.ast{
  color: hsl(169, 82%, 27%);
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