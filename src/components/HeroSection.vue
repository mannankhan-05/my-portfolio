<template>
  <section class="hero" id="home">
    <div class="container hero-container">
      <div class="hero-content">
        <h1 class="hero-title">
          <span class="greeting">Hello, I'm</span>
          <span class="name">Abdul Mannan</span>
          <span class="role">Full Stack Developer</span>
        </h1>
        <p class="hero-description">
          Crafting stunning, responsive, and user-centric web applications with
          modern technologies to turn your ideas into reality!
        </p>
        <div class="hero-actions">
          <a href="#contact" class="btn btn-primary">Get In Touch</a>
          <a href="#projects" class="btn btn-secondary">View My Work</a>
        </div>
      </div>
      <div class="hero-image">
        <div class="image-container">
          <!-- Replace with your image -->
          <div class="placeholder-image">
            <img
              :src="require('../assets/hero-image.jpg')"
              alt="Hero Image"
              class="hero-img"
            />
          </div>
        </div>
      </div>
    </div>
    <div class="scroll-indicator">
      <a href="#about" @click.prevent="scrollToSection('about')">
        <span class="scroll-arrow"></span>
      </a>
    </div>
  </section>
</template>

<script>
export default {
  name: "HeroSection",
  methods: {
    scrollToSection(sectionId) {
      this.$emit("scroll-to-section", sectionId);
    },
  },
};
</script>

<style scoped>
.hero {
  height: 100vh;
  display: flex;
  align-items: center;
  position: relative;
  padding-top: 80px;
}

.hero-container {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.hero-content {
  flex: 1;
  max-width: 600px;
}

.hero-title {
  font-size: 3.5rem;
  line-height: 1.2;
  margin-bottom: 20px;
}

.hero-title .greeting {
  display: block;
  font-size: 1.5rem;
  font-weight: 400;
  margin-bottom: 10px;
  color: var(--secondary-color);
}

.hero-title .name {
  display: block;
  font-weight: 700;
  color: var(--accent-color);
}

.hero-title .role {
  display: block;
  font-weight: 700;
}

.hero-description {
  font-size: 1.2rem;
  margin-bottom: 30px;
  color: var(--secondary-color);
}

.hero-actions {
  display: flex;
  gap: 15px;
}

.btn {
  text-decoration: none;
}

.hero-image {
  flex: 1;
  display: flex;
  justify-content: flex-end;
}

.image-container {
  width: 400px;
  height: 400px;
  border-radius: 50%;
  overflow: hidden;
  border: 5px solid var(--border-color);
}

.placeholder-image {
  width: 100%;
  height: 100%;
  background-color: #e0e0e0;
  border-radius: 8px;
  border: 1px solid var(--border-color);
}

.hero-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.scroll-indicator {
  position: absolute;
  bottom: 40px;
  left: 50%;
  transform: translateX(-50%);
}

.scroll-arrow {
  display: block;
  width: 30px;
  height: 30px;
  border-right: 3px solid var(--text-color);
  border-bottom: 3px solid var(--text-color);
  transform: rotate(45deg);
  animation: scroll-down 2s infinite;
}

@keyframes scroll-down {
  0% {
    transform: rotate(45deg) translate(0, 0);
    opacity: 0.7;
  }
  50% {
    transform: rotate(45deg) translate(10px, 10px);
    opacity: 0.2;
  }
  100% {
    transform: rotate(45deg) translate(0, 0);
    opacity: 0.7;
  }
}

@media (max-width: 992px) {
  .hero-container {
    flex-direction: column;
    text-align: center;
  }

  .hero-content {
    max-width: 100%;
    margin-bottom: 50px;
  }

  .hero-actions {
    justify-content: center;
  }
}

@media (max-width: 768px) {
  .hero-title {
    font-size: 2.5rem;
  }
}

@media (max-width: 480px) {
  .hero-title {
    font-size: 2rem;
  }

  .hero-description {
    font-size: 1rem;
  }

  .hero-actions {
    flex-direction: column;
    gap: 10px;
  }

  .btn {
    width: 100%;
  }

  .image-container {
    width: 280px;
    height: 280px;
  }
}
</style>
