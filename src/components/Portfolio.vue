<template>
    <section id="projects" class="projects-section">
      <h2 data-aos="fade-up">My Projects</h2>
  
      <!-- Project Category Buttons for Filtering -->
      <div class="project-filters" data-aos="fade-up" data-aos-delay="100">
        <button @click="filterProjects('react')" :class="{ active: activeFilter === 'react' }">React</button>
        <button @click="filterProjects('vuejs')" :class="{ active: activeFilter === 'vuejs' }">Vue.js</button>
        <button @click="filterProjects('web-design')" :class="{ active: activeFilter === 'web-design' }">Web Design</button>
      </div>
  
      <!-- Projects Grid -->
      <div class="projects-grid">
        <div v-for="(project, index) in filteredProjects" :key="index" class="project-card" @click="openProjectModal(project)">
          <div class="project-image">
            <img :src="project.image" :alt="project.title" />
          </div>
          <div class="project-info">
            <h4>{{ project.title }}</h4>
            <p>{{ project.shortDescription }}</p>
          </div>
        </div>
      </div>
  
      <!-- Project Modal (Hidden by Default) -->
      <div v-if="isModalOpen" class="project-modal" @click="closeModal">
        <div class="modal-content" @click.stop>
          <button class="close-btn" @click="closeModal">X</button>
          <h3>{{ selectedProject.title }}</h3>
          <img :src="selectedProject.image" :alt="selectedProject.title" />
          <p>{{ selectedProject.description }}</p>
          <a :href="selectedProject.demoLink" target="_blank" class="demo-link">View Demo</a>
        </div>
      </div>
    </section>
  </template>
  
  <script>
  import { gsap } from 'gsap';
  import AOS from 'aos';
  import 'aos/dist/aos.css';
  
  export default {
    data() {
      return {
        activeFilter: 'react',
        isModalOpen: false,
        selectedProject: null,
        projects: [
          {
            title: 'React Portfolio',
            image: 'https://via.placeholder.com/300x200',
            shortDescription: 'A personal portfolio website built with React.',
            description: 'A detailed React-based portfolio showcasing my work and skills.',
            demoLink: '#',
            category: 'react',
          },
          {
            title: 'React Portfolio',
            image: 'https://via.placeholder.com/300x200',
            shortDescription: 'A personal portfolio website built with React.',
            description: 'A detailed React-based portfolio showcasing my work and skills.',
            demoLink: '#',
            category: 'react',
          },
          {
            title: 'React Portfolio',
            image: 'https://via.placeholder.com/300x200',
            shortDescription: 'A personal portfolio website built with React.',
            description: 'A detailed React-based portfolio showcasing my work and skills.',
            demoLink: '#',
            category: 'react',
          },
          {
            title: 'React Portfolio',
            image: 'https://via.placeholder.com/300x200',
            shortDescription: 'A personal portfolio website built with React.',
            description: 'A detailed React-based portfolio showcasing my work and skills.',
            demoLink: '#',
            category: 'react',
          },
          {
            title: 'React Portfolio',
            image: 'https://via.placeholder.com/300x200',
            shortDescription: 'A personal portfolio website built with React.',
            description: 'A detailed React-based portfolio showcasing my work and skills.',
            demoLink: '#',
            category: 'react',
          },
          {
            title: 'Vue.js To-Do App',
            image: 'https://via.placeholder.com/300x200',
            shortDescription: 'A simple to-do list app built with Vue.js.',
            description: 'A to-do app with CRUD functionality, built using Vue.js.',
            demoLink: '#',
            category: 'vuejs',
          },
          {
            title: 'Responsive Landing Page',
            image: 'https://via.placeholder.com/300x200',
            shortDescription: 'A beautifully designed landing page.',
            description: 'A responsive, mobile-first landing page designed for marketing.',
            demoLink: '#',
            category: 'web-design',
          },
          {
            title: 'Responsive Landing Page',
            image: 'https://via.placeholder.com/300x200',
            shortDescription: 'A beautifully designed landing page.',
            description: 'A responsive, mobile-first landing page designed for marketing.',
            demoLink: '#',
            category: 'web-design',
          }
        ],
        filteredProjects: [],
      };
    },
    methods: {
      // Filter projects based on selected category
      filterProjects(category) {
        this.activeFilter = category;
        this.filteredProjects = this.projects.filter(project => project.category === category);
      },
  
      // Open project modal
      openProjectModal(project) {
        this.selectedProject = project;
        this.isModalOpen = true;
        gsap.fromTo(
          '.project-modal .modal-content',
          { scale: 0.8, opacity: 0 },
          { scale: 1, opacity: 1, duration: 0.5 }
        );
      },
  
      // Close project modal
      closeModal() {
        gsap.to('.project-modal .modal-content', { scale: 0.8, opacity: 0, duration: 0.5 });
        setTimeout(() => {
          this.isModalOpen = false;
        }, 500);
      },
    },
    mounted() {
      AOS.init();
      this.filterProjects('react'); // Default category to show on page load
    },
  };
  </script>
  
  <style scoped>
  .projects-section {
    padding: 60px 20px;
    text-align: center;
  }
  
  .project-filters {
    margin-bottom: 40px;
  }
  
  .project-filters button {
    padding: 10px 20px;
    margin: 0 10px;
    font-size: 1rem;
    background-color: transparent;
    border: 2px solid #ccc;
    cursor: pointer;
    transition: 0.3s ease;
  }
  
  .project-filters button.active {
    background-color: #007bff;
    color: white;
  }
  
  .projects-grid {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 40px;
  }
  
  .project-card {
    width: 300px;
    cursor: pointer;
    transition: transform 0.3s ease;
  }
  
  .project-card:hover {
    transform: translateY(-10px);
  }
  
  .project-image img {
    width: 100%;
    border-radius: 10px;
  }
  
  .project-info {
    margin-top: 10px;
  }
  
  .project-info h4 {
    font-size: 1.2rem;
  }
  
  .project-info p {
    font-size: 0.9rem;
    color: #666;
  }
  
  /* Project Modal Styles */
  .project-modal {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: rgba(0, 0, 0, 0.5);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 1000;
    opacity: 0;
    pointer-events: none;
    transition: opacity 0.3s ease;
  }
  
  .project-modal .modal-content {
    background-color: white;
    padding: 30px;
    border-radius: 10px;
    width: 500px;
    max-width: 90%;
    text-align: center;
    transform: scale(0.8);
    opacity: 0;
  }
  
  .project-modal .close-btn {
    position: absolute;
    top: 10px;
    right: 10px;
    background-color: transparent;
    border: none;
    font-size: 1.5rem;
    cursor: pointer;
  }
  
  .project-modal .demo-link {
    display: inline-block;
    margin-top: 20px;
    font-size: 1rem;
    color: #007bff;
    text-decoration: none;
    transition: color 0.3s ease;
  }
  
  .project-modal .demo-link:hover {
    color: #0056b3;
  }
  
  /* Hover Effects for Project Cards */
  .project-card:hover .project-info {
    opacity: 0.9;
  }
  </style>
  