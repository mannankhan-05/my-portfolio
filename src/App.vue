<template>
  <div :class="['portfolio', isDarkTheme ? 'dark-theme' : 'light-theme']">
    <Navbar
      :sections="sections"
      :isScrolled="isScrolled"
      :isDarkTheme="isDarkTheme"
      :isMenuOpen="isMenuOpen"
      @toggle-theme="toggleTheme"
      @toggle-menu="toggleMenu"
      @scroll-to-section="scrollToSection"
    />

    <HeroSection @scroll-to-section="scrollToSection" />

    <AboutSection />

    <ProjectsSection />

    <SkillsSection />

    <EducationSection />

    <ContactSection />

    <FooterSection :sections="sections" @scroll-to-section="scrollToSection" />

    <BackToTop :visible="showBackToTop" @scroll-to-top="scrollToTop" />
  </div>
</template>

<script>
import Navbar from "./components/AppNavbar.vue";
import HeroSection from "./components/HeroSection.vue";
import AboutSection from "./components/AboutSection.vue";
import ProjectsSection from "./components/ProjectsSection.vue";
import SkillsSection from "./components/SkillsSection.vue";
import EducationSection from "./components/EducationSection.vue";
import ContactSection from "./components/ContactSection.vue";
import FooterSection from "./components/FooterSection.vue";
import BackToTop from "./components/BackToTop.vue";
import "./assets/css/variables.css";

export default {
  name: "MyPortfolio",
  components: {
    Navbar,
    HeroSection,
    AboutSection,
    ProjectsSection,
    SkillsSection,
    EducationSection,
    ContactSection,
    FooterSection,
    BackToTop,
  },
  data() {
    return {
      isDarkTheme: false,
      isScrolled: false,
      isMenuOpen: false,
      showBackToTop: false,
      sections: [
        { id: "home", title: "Home" },
        { id: "about", title: "About" },
        { id: "projects", title: "Projects" },
        { id: "skills", title: "Skills" },
        { id: "education", title: "Education" },
        { id: "contact", title: "Contact" },
      ],
    };
  },
  mounted() {
    window.addEventListener("scroll", this.handleScroll);

    // Check for saved theme preference
    const savedTheme = localStorage.getItem("portfolio-theme");
    if (savedTheme) {
      this.isDarkTheme = savedTheme === "dark";
    } else {
      // Check for system preference
      const prefersDark = window.matchMedia(
        "(prefers-color-scheme: dark)"
      ).matches;
      this.isDarkTheme = prefersDark;
    }

    // Apply theme
    document.body.classList.toggle("dark-theme", this.isDarkTheme);
  },
  beforeUnmount() {
    window.removeEventListener("scroll", this.handleScroll);
  },
  methods: {
    toggleTheme() {
      this.isDarkTheme = !this.isDarkTheme;
      document.body.classList.toggle("dark-theme", this.isDarkTheme);
      localStorage.setItem(
        "portfolio-theme",
        this.isDarkTheme ? "dark" : "light"
      );
    },
    toggleMenu() {
      this.isMenuOpen = !this.isMenuOpen;
      if (this.isMenuOpen) {
        document.body.style.overflow = "hidden";
      } else {
        document.body.style.overflow = "";
      }
    },
    handleScroll() {
      this.isScrolled = window.scrollY > 50;
      this.showBackToTop = window.scrollY > 500;
    },
    scrollToSection(sectionId) {
      this.isMenuOpen = false;
      document.body.style.overflow = "";

      const element = document.getElementById(sectionId);
      if (element) {
        const offsetTop = element.offsetTop;
        window.scrollTo({
          top: offsetTop - 80, // Adjust for header height
          behavior: "smooth",
        });
      }
    },
    scrollToTop() {
      window.scrollTo({
        top: 0,
        behavior: "smooth",
      });
    },
  },
};
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: "Inter", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto,
    Oxygen, Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  line-height: 1.6;
  color: var(--text-color);
  background-color: var(--background-color);
  transition: var(--transition);
}

.portfolio {
  background-color: var(--background-color);
  color: var(--text-color);
  transition: var(--transition);
}

a {
  color: var(--accent-color);
  text-decoration: none;
  transition: var(--transition);
}

a:hover {
  color: var(--primary-color);
}
</style>
