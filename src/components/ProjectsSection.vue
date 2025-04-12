<template>
  <section class="section" id="projects">
    <div class="container">
      <h2 class="section-title">My Projects</h2>
      <div class="projects-grid">
        <div
          v-for="project in filteredProjects"
          :key="project.id"
          class="project-card"
        >
          <div class="project-image">
            <div class="carousel-container">
              <transition-group name="fade" tag="div" class="carousel">
                <div
                  v-for="(image, index) in project.images"
                  :key="index"
                  v-show="project.currentImageIndex === index"
                  class="carousel-image"
                  :style="{ backgroundColor: image.color }"
                >
                  <img
                    v-if="image.url"
                    :src="image.url"
                    :alt="`${project.title} image ${index + 1}`"
                  />
                </div>
              </transition-group>
              <div class="carousel-indicators">
                <span
                  v-for="(image, index) in project.images"
                  :key="index"
                  :class="[
                    'indicator',
                    project.currentImageIndex === index ? 'active' : '',
                  ]"
                  @click="setProjectImage(project, index)"
                ></span>
              </div>
            </div>
          </div>
          <div class="project-content">
            <h3 class="project-title">{{ project.title }}</h3>
            <p class="project-description">{{ project.description }}</p>
            <div class="project-tech">
              <span
                v-for="tech in project.technologies"
                :key="tech"
                class="tech-tag"
              >
                {{ tech }}
              </span>
            </div>
            <div class="project-links">
              <a
                :href="project.github"
                class="project-link"
                aria-label="View code on GitHub"
              >
                <i class="fab fa-github"></i>
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "ProjectsSection",
  data() {
    return {
      currentFilter: "All",
      projectFilters: ["All", "Web", "Mobile", "Backend", "UI/UX"],
      carouselIntervals: {},
      projects: [
        {
          id: 1,
          title: "NexCart",
          description:
            "A full-featured e-commerce platform with product management, cart functionality, and admin dashboard.",
          technologies: ["Vue.js", "Node.js", "Postgresql", "Express"],
          category: "Web",
          github: "https://github.com/mannankhan-05/online-store",
          demo: "#",
          currentImageIndex: 0,
          images: [
            { color: "#3498db", url: require("../assets/a1.png") },
            { color: "#2980b9", url: require("../assets/a2.png") },
            { color: "#1f6aa5", url: require("../assets/a3.png") },
            { color: "#154e7c", url: require("../assets/a4.png") },
            { color: "#0c3c5f", url: require("../assets/a5.png") },
          ],
        },
        {
          id: 2,
          title: "Thinkadoo",
          description:
            "A platform to sell e-books with user authentication, cart functionality, and payment integration.",
          technologies: ["Vue.js", "Node.js", "Postgresql", "Express"],
          category: "Mobile",
          github: "https://github.com/mannankhan-05/thinkadoo",
          demo: "#",
          currentImageIndex: 0,
          images: [
            { color: "#e74c3c", url: require("../assets/b1.png") },
            { color: "#c0392b", url: require("../assets/b2.png") },
            { color: "#a93226", url: require("../assets/b3.png") },
            { color: "#922b21", url: require("../assets/b4.png") },
            { color: "#7d3c98", url: require("../assets/b5.png") },
          ],
        },
        {
          id: 3,
          title: "Blog Application",
          description:
            "A blogging platform with user authentication, post creation, and commenting features.",
          technologies: ["Vue.js", "Node.js", "Postgresql", "Express"],
          category: "Backend",
          github: "https://github.com/mannankhan-05/blogapp-fullstack",
          demo: "#",
          currentImageIndex: 0,
          images: [
            { color: "#2ecc71", url: require("../assets/c1.png") },
            { color: "#27ae60", url: require("../assets/c2.png") },
            { color: "#1e8449", url: require("../assets/c3.png") },
            { color: "#145a32", url: require("../assets/c4.png") },
            { color: "#0e6655", url: require("../assets/c5.png") },
          ],
        },
      ],
    };
  },
  computed: {
    filteredProjects() {
      if (this.currentFilter === "All") {
        return this.projects;
      }
      return this.projects.filter(
        (project) => project.category === this.currentFilter
      );
    },
  },
  methods: {
    setProjectFilter(filter) {
      this.currentFilter = filter;
    },
    setProjectImage(project, index) {
      project.currentImageIndex = index;
    },
    nextImage(project) {
      project.currentImageIndex =
        (project.currentImageIndex + 1) % project.images.length;
    },
    startCarousels() {
      this.projects.forEach((project) => {
        this.carouselIntervals[project.id] = setInterval(() => {
          this.nextImage(project);
        }, 3000); // Change image every 3 seconds
      });
    },
    stopCarousels() {
      Object.values(this.carouselIntervals).forEach((interval) => {
        clearInterval(interval);
      });
      this.carouselIntervals = {};
    },
  },
  mounted() {
    this.startCarousels();
  },
  beforeUnmount() {
    this.stopCarousels();
  },
};
</script>

<style scoped>
.section {
  padding: 100px 0;
}

.section-title {
  font-size: 2.5rem;
  margin-bottom: 60px;
  text-align: center;
  position: relative;
}

.section-title::after {
  content: "";
  position: absolute;
  bottom: -15px;
  left: 50%;
  transform: translateX(-50%);
  width: 80px;
  height: 4px;
  background-color: var(--accent-color);
}

.projects-filter {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 15px;
  margin-bottom: 40px;
}

.filter-btn {
  padding: 8px 20px;
  background-color: var(--icon-background);
  border: 1px solid var(--border-color);
  border-radius: 30px;
  cursor: pointer;
  font-size: 0.9rem;
  transition: all 0.3s ease;
  color: var(--primary-color);
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
}

.filter-btn:hover {
  background-color: var(--border-color);
}

.filter-btn.active {
  background-color: var(--accent-color);
  color: white;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 30px;
}

.project-card {
  background-color: var(--surface-color);
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 5px 15px var(--shadow-color);
  transition: all 0.3s ease;
  border: var(--card-border);
}

.project-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 15px 30px var(--shadow-color);
}

.project-image {
  height: 200px;
}

.carousel-container {
  position: relative;
  width: 100%;
  height: 100%;
  overflow: hidden;
}

.carousel {
  width: 100%;
  height: 100%;
  position: relative;
}

.carousel-image {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}

.carousel-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.carousel-indicators {
  position: absolute;
  bottom: 10px;
  left: 0;
  right: 0;
  display: flex;
  justify-content: center;
  gap: 8px;
  z-index: 10;
}

.indicator {
  width: 10px;
  height: 10px;
  border-radius: 50%;
  background-color: rgba(255, 255, 255, 0.5);
  cursor: pointer;
  transition: all 0.3s ease;
}

.indicator.active {
  background-color: white;
  transform: scale(1.2);
}

/* Transition animations */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

.project-content {
  padding: 20px;
}

.project-title {
  font-size: 1.3rem;
  margin-bottom: 10px;
}

.project-description {
  color: var(--secondary-color);
  margin-bottom: 15px;
  font-size: 0.95rem;
}

.project-tech {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-bottom: 15px;
}

.tech-tag {
  padding: 5px 10px;
  background-color: var(--icon-background);
  border-radius: 20px;
  font-size: 0.8rem;
  border: 1px solid var(--border-color);
  color: var(--primary-color);
  box-shadow: 0 1px 2px rgba(0, 0, 0, 0.1);
}

.project-links {
  display: flex;
  gap: 15px;
}

.project-link {
  font-size: 2rem;
  color: var(--text-color);
}

.project-link:hover {
  color: var(--accent-color);
}

@media (max-width: 768px) {
  .section {
    padding: 70px 0;
  }

  .section-title {
    font-size: 2rem;
    margin-bottom: 40px;
  }

  .projects-grid {
    grid-template-columns: 1fr;
  }
}
</style>
