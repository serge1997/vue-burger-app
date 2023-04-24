<template>
  <div class="main-container">
    <Banner />
    <h1>Monte seu Burger: </h1>
    <BurgerForm />
  </div>
</template>

<script>

import Banner from '../components/Banner.vue'
import BurgerForm from '../components/BurgerForm.vue'


export default {
  name: 'HomeView',
  components: {
    Banner,
    BurgerForm
  }
}
</script>
