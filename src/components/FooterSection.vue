<template>
    <footer id="footer" class="footer">
      <div class="footer-content">
        <!-- Social Media Icons -->
        <div class="social-icons" v-show="showFooter" @mouseenter="showFooter = true" @mouseleave="showFooter = false">
          <a href="https://facebook.com" target="_blank" class="social-icon" :class="{'animate': showFooter}">
            <i class="fab fa-facebook-f"></i>
          </a>
          <a href="https://instagram.com" target="_blank" class="social-icon" :class="{'animate': showFooter}">
            <i class="fab fa-instagram"></i>
          </a>
          <a href="https://linkedin.com" target="_blank" class="social-icon" :class="{'animate': showFooter}">
            <i class="fab fa-linkedin-in"></i>
          </a>
        </div>
  
        <!-- Newsletter Subscription Form -->
        <div class="newsletter">
          <h3>Subscribe to Our Newsletter</h3>
          <form @submit.prevent="subscribe">
            <input v-model="email" type="email" placeholder="Enter your email" required />
            <button type="submit" :disabled="!email">Subscribe</button>
          </form>
        </div>
      </div>
    </footer>
  </template>
  
  <script>
  export default {
    name: FooterSection,
    data() {
      return {
        email: '',
        showFooter: false,
      };
    },
    methods: {
      subscribe() {
        if (this.email) {
          alert('Subscribed successfully!');
          this.email = '';  // Clear input after submitting
        }
      },
    },
  };
  </script>
  
  <style scoped>
  /* Sticky Footer */
  .footer {
    /* position: fixed; */
    bottom: 0;
    left: 0;
    right: 0;
    background-color: #333;
    color: white;
    padding: 20px 0;
    text-align: center;
    z-index: 10001;
    transform: translateY(100%);
    opacity: 0;
    transition: transform 0.5s ease, opacity 0.5s ease;
  }
  
  .footer-content {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 20px;
  }
  
  .footer.show {
    transform: translateY(0);
    opacity: 1;
  }
  
  /* Social Media Icons */
  .social-icons {
    margin-bottom: 20px;
  }
  
  .social-icon {
    font-size: 1.5rem;
    margin: 0 15px;
    color: white;
    transition: transform 0.3s ease, color 0.3s ease;
  }
  
  .social-icon.animate:hover {
    transform: rotate(360deg);
    color: #007bff; /* Example color change */
  }
  
  .social-icon i {
    font-size: 2rem;
  }
  
  /* Newsletter Subscription */
  .newsletter h3 {
    margin-bottom: 10px;
    color: white;
  }
  
  .newsletter form {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  
  .newsletter input {
    padding: 10px;
    margin-right: 10px;
    border-radius: 5px;
    border: 1px solid #ccc;
    outline: none;
    font-size: 1rem;
    transition: all 0.3s ease;
  }
  
  .newsletter input:focus {
    border-color: #007bff;
    transform: scale(1.05);
  }
  
  .newsletter button {
    padding: 10px 20px;
    font-size: 1rem;
    background-color: #007bff;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: all 0.3s ease;
  }
  
  .newsletter button:disabled {
    background-color: #ccc;
    cursor: not-allowed;
  }
  
  .newsletter button:hover {
    background-color: #0056b3;
  }
  </style>
  