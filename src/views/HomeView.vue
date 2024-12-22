<template>
  <div id="main">
   
    <HeroSection/>
    <About/>
    <SkillsSection/>
    <Portfolio/>
    
    <!-- Other sections go here -->
  </div>
</template>

<script>
import About from '@/components/About.vue';
import HeroSection from '../components/HeroSection.vue';
import SkillsSection from '@/components/SkillsSection.vue';
import Portfolio from '@/components/Portfolio.vue';



export default {
  name: 'Home',
  components: {
    HeroSection,
    About,
    SkillsSection,
    Portfolio,
  }
}
</script>