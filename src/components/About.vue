<template>
    <section id="about" class="about-section">
      <div class="about-content">
        <div class="about-photo" 
             @mouseover="hoverEffect(true)" 
             @mouseleave="hoverEffect(false)"
             :class="{'zoom-in': hover}">
          <img src="https://picsum.photos/536/354" alt="Your Photo" />
        </div>
  
        <div class="about-text">
          <h2 data-aos="fade-up">Hi, I'm [Your Name]</h2>
          <p data-aos="fade-up" data-aos-delay="100">A passionate web developer focused on creating beautiful and functional websites.</p>
  
          <!-- Timeline -->
          <div class="timeline" data-aos="fade-up" data-aos-delay="200">
            <div class="timeline-item" v-for="(milestone, index) in milestones" :key="index" :data-aos="'zoom-in'" :data-aos-delay="300 + (index * 200)">
              <h4>{{ milestone.year }}</h4>
              <p>{{ milestone.description }}</p>
            </div>
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
        hover: false,
        milestones: [
          { year: '2021', description: 'Started my web development journey.' },
          { year: '2022', description: 'Built my first portfolio website.' },
          { year: '2023', description: 'Worked on several freelance projects.' },
          { year: '2024', description: 'Launched my first full-stack application.' }
        ]
      };
    },
    methods: {
      hoverEffect(isHovering) {
        this.hover = isHovering;
        if (isHovering) {
          gsap.to(".about-photo img", { scale: 1.1, duration: 0.3 });
        } else {
          gsap.to(".about-photo img", { scale: 1, duration: 0.3 });
        }
      }
    },
    mounted() {
      // Initialize AOS
      AOS.init();
    }
  };
  </script>
  
  <style scoped>
  .about-section {
    display: flex;
    justify-content: space-between;
    padding: 50px 20px;
    background-color: #f4f4f4;
  }
  
  .about-content {
    display: flex;
    flex-direction: row;
    gap: 20px;
  }
  
  .about-photo {
    position: relative;
    width: 200px;
    height: 200px;
    overflow: hidden;
    border-radius: 50%;
  }
  
  .about-photo img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform 0.3s ease;
  }
  
  .about-text {
    max-width: 600px;
  }
  
  .about-text h2 {
    font-size: 2rem;
    margin-bottom: 20px;
  }
  
  .about-text p {
    font-size: 1.1rem;
    color: #333;
  }
  
  .timeline {
    margin-top: 30px;
  }
  
  .timeline-item {
    margin-bottom: 20px;
  }
  
  .timeline-item h4 {
    font-weight: bold;
    font-size: 1.3rem;
  }
  
  .timeline-item p {
    font-size: 1.1rem;
    color: #666;
  }
  
  /* Hover effect for photo */
  .zoom-in {
    transform: scale(1.1);
  }
  
  /* AOS styles */
  [data-aos="fade-up"] {
    opacity: 0;
    transform: translateY(20px);
    transition: opacity 0.6s ease, transform 0.6s ease;
  }
  
  [data-aos="fade-up"].aos-animate {
    opacity: 1;
    transform: translateY(0);
  }
  
  [data-aos="zoom-in"] {
    opacity: 0;
    transform: scale(0.8);
    transition: opacity 0.6s ease, transform 0.6s ease;
  }
  
  [data-aos="zoom-in"].aos-animate {
    opacity: 1;
    transform: scale(1);
  }
  </style>
  
  