<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/auw_211_logo.png">
    <h1> AUW 211 Data (Report) Request Form</h1>
    <contact-form />
  </div>
</template>
<script type="text/javascript"
        src="https://cdn.jsdelivr.net/npm/emailjs-com@2/dist/email.min.js">
</script>
<script type="text/javascript">
   (function(){
      emailjs.init("user_0K7gji1oiihV7OqyPPlTZ");
   })();
</script>
<script>
import ContactForm from './components/ContactForm.vue'

export default {
  name: 'App',
  components: {
    ContactForm
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>