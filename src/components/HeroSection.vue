<template>
  <section class="hero">
    <!-- Full-Screen Parallax Background -->
    <div class="parallax-background"></div>

    <!-- Hero Content -->
    <div class="hero-content">
      <h1 class="hero-title">Hi, I'm [Your Name]</h1>
      <p class="hero-subtitle">A Web Developer | Designer | Creator</p>

      <!-- CTA Buttons -->
      <div class="hero-buttons">
        <button class="cta-btn" @click="scrollToSection">Get Started</button>
        <button class="cta-btn secondary">View My Work</button>
      </div>

      <!-- Scroll Indicator -->
      <div class="scroll-indicator" @click="scrollToSection">
        <span>Scroll Down</span>
        <svg class="arrow" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><path d="M12 21V3M5 14l7 7 7-7" /></svg>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "Hero",
  methods: {
    scrollToSection() {
      const nextSection = document.querySelector("#about");
      window.scrollTo({
        top: nextSection.offsetTop,
        behavior: "smooth",
      });
    },
  },
};
</script>

<style scoped>
.hero {
  position: relative;
  height: 100vh; /* Full screen */
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}

.parallax-background {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: url('https://picsum.photos/536/354') no-repeat center center;
  background-size: cover;
  transform: translateZ(0); /* Enable hardware acceleration for smooth effect */
  will-change: transform; /* Optimize for performance */
  animation: parallax 10s linear infinite;
}

.hero-content {
  text-align: center;
  color: rgb(255, 255, 255);
  padding: 0 20px;
  z-index: 1;
  opacity: 0;
  animation: fadeIn 2s forwards 0.5s; /* Fade-in effect with delay */
}

.hero-title {
  font-size: 3rem;
  font-weight: bold;
  margin-bottom: 20px;
  animation: typing 2.5s steps(30) 1 normal both, fadeInText 2s ease-out 0.5s forwards;
  white-space: nowrap;
  overflow: hidden;
}

.hero-subtitle {
  font-size: 1.5rem;
  margin-bottom: 30px;
  animation: fadeInText 3s ease-out 2.5s forwards;
}

.hero-buttons {
  display: flex;
  gap: 20px;
  justify-content: center;
  margin-bottom: 40px;
}

.cta-btn {
  padding: 15px 30px;
  font-size: 1.1rem;
  cursor: pointer;
  border: none;
  background-color: #ff5722;
  color: white;
  border-radius: 5px;
  transition: background-color 0.3s;
}

.cta-btn:hover {
  background-color: #e64a19;
}

.cta-btn.secondary {
  background-color: transparent;
  border: 2px solid white;
  color: white;
}

.cta-btn.secondary:hover {
  background-color: white;
  color: #ff5722;
}

.scroll-indicator {
  margin-top: 20px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  opacity: 0;
  animation: fadeInText 2s ease-out 4.5s forwards;
}

.scroll-indicator span {
  margin-right: 10px;
}

.arrow {
  width: 24px;
  height: 24px;
  stroke: white;
  animation: bounceArrow 1.5s infinite;
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

@keyframes fadeInText {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

@keyframes typing {
  0% {
    width: 0;
  }
  100% {
    width: 100%;
  }
}

@keyframes parallax {
  0% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(10%);
  }
  100% {
    transform: translateY(0);
  }
}

@keyframes bounceArrow {
  0%, 100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(10px);
  }
}
</style>
