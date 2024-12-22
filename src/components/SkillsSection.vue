<template>
    <section id="skills" class="skills-section">
      <h2 data-aos="fade-up">My Skills</h2>
  
      <!-- Skill Category Buttons for Sorting -->
      <div class="skills-filters" data-aos="fade-up" data-aos-delay="100">
        <button @click="filterSkills('frontend')" :class="{ active: activeFilter === 'frontend' }">Front-End</button>
        <button @click="filterSkills('backend')" :class="{ active: activeFilter === 'backend' }">Back-End</button>
        <button @click="filterSkills('design')" :class="{ active: activeFilter === 'design' }">Design</button>
      </div>
  
      <!-- Skill Items (with progress bars and icons) -->
      <div class="skills-list" v-if="filteredSkills.length">
        <div v-for="(skill, index) in filteredSkills" :key="index" class="skill-item">
          <div class="skill-icon" @mouseover="hoverEffect(true, index)" @mouseleave="hoverEffect(false, index)">
            <img :src="skill.icon" :alt="skill.name" />
          </div>
  
          <div class="skill-name">
            <h4>{{ skill.name }}</h4>
            <p>{{ skill.level }}%</p>
          </div>
  
          <!-- Animated Progress Bar -->
          <div class="progress-bar" data-aos="fade-up">
            <div class="bar" :style="{ width: skill.level + '%' }"></div>
          </div>
        </div>
      </div>
    </section>
  </template>
  
  <script>
  import { gsap } from "gsap";
  import AOS from 'aos';
  import 'aos/dist/aos.css';
  
  export default {
    data() {
      return {
        activeFilter: 'frontend',
        skills: [
          { name: 'HTML', level: 90, icon: 'https://img.icons8.com/color/48/000000/html-5.png', category: 'frontend' },
          { name: 'CSS', level: 80, icon: 'https://img.icons8.com/color/48/000000/css3.png', category: 'frontend' },
          { name: 'JavaScript', level: 85, icon: 'https://img.icons8.com/color/48/000000/javascript.png', category: 'frontend' },
          { name: 'Node.js', level: 75, icon: 'https://img.icons8.com/color/48/000000/nodejs.png', category: 'backend' },
          { name: 'React', level: 80, icon: 'https://img.icons8.com/color/48/000000/react-native.png', category: 'frontend' },
          { name: 'Vue.js', level: 70, icon: 'https://img.icons8.com/color/48/000000/vuejs.png', category: 'frontend' },
          { name: 'Git', level: 90, icon: 'https://img.icons8.com/color/48/000000/git.png', category: 'backend' },
          { name: 'UI/UX Design', level: 70, icon: 'https://img.icons8.com/color/48/000000/graphic-design.png', category: 'design' },
        ],
        filteredSkills: [],
      };
    },
    methods: {
      // Filter skills based on category
      filterSkills(category) {
        this.activeFilter = category;
        this.filteredSkills = this.skills.filter(skill => skill.category === category);
      },
  
      // Hover effect for icons
      hoverEffect(isHovering, index) {
        const scaleValue = isHovering ? 1.1 : 1;
        gsap.to(`.skill-icon:nth-child(${index + 1}) img`, { scale: scaleValue, duration: 0.3 });
      },
    },
    mounted() {
      AOS.init();
      this.filterSkills('frontend'); // Default to showing frontend skills
    },
  };
  </script>
  
  <style scoped>
  .skills-section {
    padding: 60px 20px;
    text-align: center;
  }
  
  .skills-filters {
    margin-bottom: 40px;
  }
  
  .skills-filters button {
    padding: 10px 20px;
    margin: 0 10px;
    font-size: 1rem;
    background-color: transparent;
    border: 2px solid #ccc;
    cursor: pointer;
    transition: 0.3s ease;
  }
  
  .skills-filters button.active {
    background-color: #007bff;
    color: white;
  }
  
  .skills-list {
    display: flex;
    justify-content: center;
    gap: 40px;
    flex-wrap: wrap;
  }
  
  .skill-item {
    width: 150px;
    text-align: center;
  }
  
  .skill-icon img {
    width: 50px;
    height: 50px;
    transition: transform 0.3s ease;
  }
  
  .skill-name h4 {
    font-size: 1.1rem;
    margin-top: 10px;
  }
  
  .skill-name p {
    font-size: 0.9rem;
    color: #666;
  }
  
  /* Progress Bar Styles */
  .progress-bar {
    margin-top: 20px;
    height: 10px;
    background-color: #e0e0e0;
    border-radius: 5px;
  }
  
  .progress-bar .bar {
    height: 100%;
    background-color: #007bff;
    border-radius: 5px;
    transition: width 1s ease-out;
  }
  
  /* Hover Effects */
  .skill-icon img:hover {
    filter: drop-shadow(0 0 10px rgba(0, 123, 255, 0.8));
  }
  </style>
  
  