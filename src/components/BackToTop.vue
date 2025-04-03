<template>
  <button
    @click="scrollToTop"
    class="back-to-top"
    :class="{ visible: visible }"
    aria-label="Back to top"
  >
    <i class="fas fa-arrow-up"></i>
  </button>
</template>

<script>
export default {
  name: "BackToTop",
  props: {
    visible: {
      type: Boolean,
      default: false,
    },
  },
  methods: {
    scrollToTop() {
      this.$emit("scroll-to-top");
    },
  },
};
</script>

<style scoped>
.back-to-top {
  position: fixed;
  bottom: 30px;
  right: 30px;
  width: 50px;
  height: 50px;
  border-radius: 50%;
  background-color: var(--accent-color);
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  opacity: 0;
  visibility: hidden;
  transition: all 0.3s ease;
  border: none;
  z-index: 999;
}

.back-to-top.visible {
  opacity: 1;
  visibility: visible;
}

.back-to-top:hover {
  background-color: #005bb5;
}
</style>
