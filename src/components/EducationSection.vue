<template>
  <section class="section" id="education">
    <div class="container">
      <h2 class="section-title">Education</h2>
      <div class="timeline">
        <div
          class="timeline-item"
          v-for="(item, index) in timeline"
          :key="index"
        >
          <div class="timeline-dot"></div>
          <div class="timeline-date">{{ item.period }}</div>
          <div class="timeline-content">
            <h3 class="timeline-title">{{ item.title }}</h3>
            <h4 class="timeline-subtitle">{{ item.organization }}</h4>
            <p class="timeline-description">{{ item.description }}</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "EducationSection",
  data() {
    return {
      timeline: [
        {
          period: "2022 - 2026",
          title: "Bachelor of Science in Computer Science",
          organization: "University of Karachi",
          description:
            "Currently pursuing a degree in Computer Science, focusing on software development and data science.",
        },
        {
          period: "2020 - 2022",
          title: "Intermediate in Computer Science",
          organization: "National College",
          description:
            "Completed my intermediate education with a focus on computer science and mathematics.",
        },
        {
          period: "2018 - 2020",
          title: "Matriculation in Science",
          organization: "Karachi Board",
          description:
            "Completed my matriculation with a strong foundation in science subjects.",
        },
      ],
    };
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

.timeline {
  position: relative;
  max-width: 800px;
  margin: 0 auto;
}

.timeline::before {
  content: "";
  position: absolute;
  top: 0;
  left: 20px;
  height: 100%;
  width: 2px;
  background-color: #777;
}

.timeline-item {
  position: relative;
  padding-left: 60px;
  margin-bottom: 50px;
}

.timeline-item:last-child {
  margin-bottom: 0;
}

.timeline-dot {
  position: absolute;
  left: 16px;
  top: 5px;
  width: 10px;
  height: 10px;
  border-radius: 50%;
  background-color: var(--accent-color);
  border: 2px solid white;
  box-shadow: 0 0 0 1px var(--border-color);
}

.timeline-date {
  font-size: 0.9rem;
  font-weight: 600;
  color: var(--accent-color);
  margin-bottom: 5px;
}

.timeline-title {
  font-size: 1.3rem;
  margin-bottom: 5px;
}

.timeline-subtitle {
  font-size: 1rem;
  color: var(--secondary-color);
  margin-bottom: 10px;
}

.timeline-description {
  color: var(--secondary-color);
}

@media (max-width: 768px) {
  .section {
    padding: 70px 0;
  }

  .section-title {
    font-size: 2rem;
    margin-bottom: 40px;
  }
}

@media (max-width: 480px) {
  .timeline::before {
    left: 15px;
  }

  .timeline-item {
    padding-left: 45px;
  }

  .timeline-dot {
    left: 11px;
  }
}
</style>
