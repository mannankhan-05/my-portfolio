<template>
  <footer class="footer">
    <div class="container">
      <div class="footer-content">
        <div class="footer-logo">
          <span class="logo-text">DEV</span>
        </div>
        <p class="footer-text">
          &copy; {{ new Date().getFullYear() }} Managed and developed by
          <a href="https://github.com/mannanKhan-05">Abdul Mannan</a>
        </p>
        <div class="footer-links">
          <a
            v-for="section in sections"
            :key="section.id"
            :href="`#${section.id}`"
            @click="scrollToSection(section.id)"
            class="footer-link"
          >
            {{ section.title }}
          </a>
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: "FooterSection",
  props: {
    sections: {
      type: Array,
      required: true,
    },
  },
  methods: {
    scrollToSection(sectionId) {
      this.$emit("scroll-to-section", sectionId);
    },
  },
};
</script>

<style scoped>
.footer {
  background-color: var(--surface-color);
  padding: 40px 0;
  margin-top: 100px;
  border-top: 1px solid var(--border-color);
}

.footer-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  gap: 20px;
}

.logo-text {
  color: var(--accent-color);
  font-size: 1.8rem;
  font-weight: 700;
}

.footer-text {
  color: var(--secondary-color);
}

.footer-links {
  display: flex;
  gap: 20px;
  flex-wrap: wrap;
  justify-content: center;
}

.footer-link {
  color: var(--text-color);
  text-decoration: none;
}

.footer-link:hover {
  color: var(--accent-color);
}
</style>
