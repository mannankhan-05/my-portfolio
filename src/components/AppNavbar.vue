<template>
  <nav class="nav" :class="{ 'nav-scrolled': isScrolled }">
    <div class="container nav-container">
      <div class="logo">
        <span class="logo-text">DEV</span>
      </div>
      <div class="nav-links" :class="{ 'nav-active': isMenuOpen }">
        <a
          v-for="section in sections"
          :key="section.id"
          :href="`#${section.id}`"
          @click="scrollToSection(section.id)"
          class="nav-link"
        >
          {{ section.title }}
        </a>
      </div>
      <div class="nav-actions">
        <button
          @click="toggleTheme"
          class="theme-toggle"
          :aria-label="
            isDarkTheme ? 'Switch to light theme' : 'Switch to dark theme'
          "
        >
          <span v-if="isDarkTheme" class="theme-icon">☀️</span>
          <span v-else class="theme-icon">🌙</span>
        </button>
        <button @click="toggleMenu" class="menu-toggle">
          <span class="menu-icon"></span>
        </button>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  name: "AppNavbar",
  props: {
    sections: {
      type: Array,
      required: true,
    },
    isScrolled: {
      type: Boolean,
      default: false,
    },
    isDarkTheme: {
      type: Boolean,
      default: false,
    },
    isMenuOpen: {
      type: Boolean,
      default: false,
    },
  },
  methods: {
    toggleTheme() {
      this.$emit("toggle-theme");
    },
    toggleMenu() {
      this.$emit("toggle-menu");
    },
    scrollToSection(sectionId) {
      this.$emit("scroll-to-section", sectionId);
    },
  },
};
</script>

<style scoped>
.nav {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 1000;
  padding: 20px 0;
  transition: all 0.3s ease;
}

.nav-scrolled {
  background-color: var(--background-color);
  box-shadow: 0 2px 10px var(--shadow-color);
  padding: 15px 0;
  border-bottom: 1px solid var(--border-color);
}

.nav-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.logo {
  font-size: 1.8rem;
  font-weight: 700;
}

.logo-text {
  color: var(--accent-color);
}

.nav-links {
  display: flex;
  gap: 30px;
}

.nav-link {
  color: var(--text-color);
  font-weight: 500;
  position: relative;
  text-decoration: none;
}

.nav-link::after {
  content: "";
  position: absolute;
  bottom: -5px;
  left: 0;
  width: 0;
  height: 2px;
  background-color: var(--accent-color);
  transition: all 0.3s ease;
}

.nav-link:hover::after {
  width: 100%;
}

.nav-actions {
  display: flex;
  align-items: center;
  gap: 20px;
}

.theme-toggle {
  background: none;
  border: none;
  cursor: pointer;
  font-size: 1.2rem;
}

.menu-toggle {
  display: none;
  background: none;
  border: none;
  cursor: pointer;
  width: 30px;
  height: 20px;
  position: relative;
}

.menu-icon,
.menu-icon::before,
.menu-icon::after {
  position: absolute;
  width: 30px;
  height: 2px;
  background-color: var(--text-color);
  transition: all 0.3s ease;
}

.menu-icon {
  top: 50%;
  transform: translateY(-50%);
}

.menu-icon::before,
.menu-icon::after {
  content: "";
  left: 0;
}

.menu-icon::before {
  top: -8px;
}

.menu-icon::after {
  bottom: -8px;
}

@media (max-width: 768px) {
  .menu-toggle {
    display: block;
  }

  .nav-links {
    position: fixed;
    top: 0;
    right: -100%;
    width: 80%;
    max-width: 400px;
    height: 100vh;
    background-color: var(--background-color);
    flex-direction: column;
    justify-content: center;
    align-items: center;
    transition: all 0.3s ease;
    z-index: 1001;
    box-shadow: -5px 0 15px var(--shadow-color);
  }

  .nav-links.nav-active {
    right: 0;
  }

  .nav-link {
    font-size: 1.2rem;
    padding: 15px 0;
  }
}
</style>
