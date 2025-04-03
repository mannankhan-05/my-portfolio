<template>
  <section class="section" id="projects">
    <div class="container">
      <h2 class="section-title">My Projects</h2>
      <div class="projects-filter">
        <button
          v-for="filter in projectFilters"
          :key="filter"
          @click="setProjectFilter(filter)"
          :class="['filter-btn', currentFilter === filter ? 'active' : '']"
        >
          {{ filter }}
        </button>
      </div>
      <div class="projects-grid">
        <div
          v-for="project in filteredProjects"
          :key="project.id"
          class="project-card"
        >
          <div class="project-image">
            <div
              class="placeholder-image"
              :style="{ backgroundColor: project.color }"
            ></div>
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
              <a
                :href="project.demo"
                class="project-link"
                aria-label="View live demo"
              >
                <i class="fas fa-external-link-alt"></i>
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
      projects: [
        {
          id: 1,
          title: "E-Commerce Platform",
          description:
            "A full-featured e-commerce platform with product management, cart functionality, and payment processing.",
          technologies: ["React", "Node.js", "MongoDB", "Express"],
          category: "Web",
          github: "#",
          demo: "#",
          color: "#3498db",
        },
        {
          id: 2,
          title: "Task Management App",
          description:
            "A mobile application for managing tasks, setting reminders, and tracking productivity.",
          technologies: ["React Native", "Firebase", "Redux"],
          category: "Mobile",
          github: "#",
          demo: "#",
          color: "#e74c3c",
        },
        {
          id: 3,
          title: "API Gateway Service",
          description:
            "A microservice architecture API gateway that handles routing, authentication, and rate limiting.",
          technologies: ["Node.js", "Express", "Docker", "Kubernetes"],
          category: "Backend",
          github: "#",
          demo: "#",
          color: "#2ecc71",
        },
        {
          id: 4,
          title: "Portfolio Website",
          description:
            "A responsive portfolio website with modern design principles and animations.",
          technologies: ["Vue.js", "SCSS", "GSAP"],
          category: "UI/UX",
          github: "#",
          demo: "#",
          color: "#9b59b6",
        },
        {
          id: 5,
          title: "Real-time Chat Application",
          description:
            "A real-time messaging platform with private and group chat functionality.",
          technologies: ["Socket.io", "React", "Node.js", "MongoDB"],
          category: "Web",
          github: "#",
          demo: "#",
          color: "#f39c12",
        },
        {
          id: 6,
          title: "Data Visualization Dashboard",
          description:
            "An interactive dashboard for visualizing complex datasets with filtering capabilities.",
          technologies: ["D3.js", "Vue.js", "Express", "PostgreSQL"],
          category: "Web",
          github: "#",
          demo: "#",
          color: "#1abc9c",
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
  grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
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

.placeholder-image {
  width: 100%;
  height: 100%;
  background-color: #e0e0e0;
  border-radius: 0;
  border: none;
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
  font-size: 1.2rem;
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
