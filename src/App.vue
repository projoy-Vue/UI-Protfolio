<template>
  <div id="app">
    <Navbar/>
   <RouterView/>
  </div>
</template>

<script>

import Navbar from '@/components/Navbar.vue';
// import FooterSection from '@/components/FooterSection.vue'; // Adjust the path if necessary


export default {
  name: 'App',
  components: {
    Navbar,
    // FooterSection
  }
}
</script>


<style scoped>

</style>