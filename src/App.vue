<template>

  <Navbar :logo="logo_src" :alt="app_name" />

  <router-view/>
  
  <Footer/>
  
</template>

<script>

import Navbar from './components/Navbar.vue'
import Footer from './components/Footer.vue'

  export default{

    components: {
      Navbar,
      Footer
    },

    data() {

      return {
        logo_src: '/img/logo.png',
        app_name: 'App Burger'
      }
    }
  }
</script>
<style>

  * {
    padding: 0;
    margin: 0;
    font-family: Helvetica, sans-serif;
    box-sizing: border-box;
  }

  .main-container {
    margin: auto;
    min-height: 270px;
  }

  h1 {
    text-align: center;
    font-size: 42px;
    color: #222;
    margin-bottom: 32px;
  }


</style>
