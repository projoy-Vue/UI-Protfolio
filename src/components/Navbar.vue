<template>
    <header>
      <!-- Navbar -->
      <nav class="navbar" :class="{'scrolled': isScrolled}">
        <div class="logo">
          <a href="#hero">[Your Logo]</a>
        </div>
        
        <!-- Desktop Menu -->
        <ul class="nav-links">
          <li><a href="#about" :class="{'active': activeLink === 'about'}">About</a></li>
          <li><a href="#portfolio" :class="{'active': activeLink === 'portfolio'}">Portfolio</a></li>
          <li><a href="#contact" :class="{'active': activeLink === 'contact'}">Contact</a></li>
        </ul>
  
        <!-- Mobile Hamburger Menu -->
        <div class="hamburger" @click="toggleMobileMenu">
          <span></span>
          <span></span>
          <span></span>
        </div>
      </nav>
  
      <!-- Mobile Fullscreen Menu -->
      <div class="mobile-menu" v-if="mobileMenuOpen">
        <div class="close-btn" @click="toggleMobileMenu">X</div>
        <ul>
          <li><a href="#about" @click="setActiveLink('about')">About</a></li>
          <li><a href="#portfolio" @click="setActiveLink('portfolio')">Portfolio</a></li>
          <li><a href="#contact" @click="setActiveLink('contact')">Contact</a></li>
        </ul>
      </div>
    </header>
  </template>
  
  <script>
  export default {
    data() {
      return {
        isScrolled: false,
        mobileMenuOpen: false,
        activeLink: '',
      };
    },
    methods: {
      toggleMobileMenu() {
        this.mobileMenuOpen = !this.mobileMenuOpen;
      },
      setActiveLink(section) {
        this.activeLink = section;
        if (this.mobileMenuOpen) {
          this.mobileMenuOpen = false;
        }
      },
      handleScroll() {
        if (window.scrollY > 50) {
          this.isScrolled = true;
        } else {
          this.isScrolled = false;
        }
      }
    },
    mounted() {
      window.addEventListener('scroll', this.handleScroll);
    },
    beforeDestroy() {
      window.removeEventListener('scroll', this.handleScroll);
    }
  };
  </script>
  
  <style scoped>
  /* Navbar Styles */
  .navbar {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    width: 100%;
    padding: 20px;
    background: transparent;
    transition: background-color 0.3s ease, box-shadow 0.3s ease;
    z-index: 1000;
    display: flex;
    justify-content: space-between;
    align-items: center;
    box-shadow: none;
  }
  
  .navbar.scrolled {
    background-color: #333; /* Solid background when scrolled */
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); /* Add shadow when scrolled */
  }
  
  .navbar .logo a {
    font-size: 1.5rem;
    color: white;
    text-decoration: none;
  }
  
  .navbar .nav-links {
    list-style: none;
    display: flex;
    gap: 20px;
  }
  
  .navbar .nav-links li a {
    color: white;
    text-decoration: none;
    font-size: 1.1rem;
    position: relative;
    padding: 5px;
    transition: color 0.3s ease;
  }
  
  .navbar .nav-links li a.active {
    color: #ff5722; /* Active link color */
  }
  
  .navbar .nav-links li a.active::after {
    content: '';
    position: absolute;
    bottom: -3px;
    left: 0;
    width: 100%;
    height: 2px;
    background-color: #ff5722;
    animation: underlineAnimation 0.3s ease-out;
  }
  
  @keyframes underlineAnimation {
    0% {
      width: 0;
    }
    100% {
      width: 100%;
    }
  }
  
  /* Hamburger Menu (Mobile) */
  .hamburger {
    display: none;
    cursor: pointer;
    flex-direction: column;
    gap: 5px;
  }
  
  .hamburger span {
    width: 25px;
    height: 3px;
    background-color: white;
    border-radius: 5px;
  }
  
  /* Mobile Menu (Fullscreen) */
  .mobile-menu {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.8); /* Dark background with slight transparency */
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;
    z-index: 1001;
    animation: slideIn 0.3s ease-in-out; /* Slide-in effect */
  }
  
  @keyframes slideIn {
    from {
      transform: translateX(-100%);
    }
    to {
      transform: translateX(0);
    }
  }
  
  .mobile-menu ul {
    list-style: none;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 100%;
    gap: 40px;
    margin-top: 100px; /* Space from top */
  }
  
  .mobile-menu ul li a {
    font-size: 1.5rem;
    color: white;
    text-decoration: none;
    padding: 15px 0;
    text-transform: uppercase;
    letter-spacing: 1px;
    transition: color 0.3s ease;
  }
  
  .mobile-menu ul li a:hover {
    color: #ff5722; /* Hover effect */
  }
  
  .close-btn {
    position: absolute;
    top: 20px;
    right: 20px;
    font-size: 2rem;
    color: white;
    cursor: pointer;
    background-color: transparent;
    border: none;
    transition: color 0.3s ease;
  }
  
  .close-btn:hover {
    color: #ff5722; /* Close button hover color */
  }
  
  /* Responsive Styles */
  @media (max-width: 768px) {
    .navbar .nav-links {
      display: none;
    }
  
    .hamburger {
      display: flex;
    }
  }
  </style>
  
  