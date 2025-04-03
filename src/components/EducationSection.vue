<template>
  <section class="section" id="education">
    <div class="container">
      <h2 class="section-title">Education & Experience</h2>
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
          period: "2020 - Present",
          title: "Senior Full Stack Developer",
          organization: "Tech Innovations Inc.",
          description:
            "Leading development of enterprise web applications, mentoring junior developers, and implementing CI/CD pipelines.",
        },
        {
          period: "2018 - 2020",
          title: "Full Stack Developer",
          organization: "Digital Solutions LLC",
          description:
            "Developed and maintained multiple client projects using React, Node.js, and MongoDB. Implemented responsive designs and RESTful APIs.",
        },
        {
          period: "2016 - 2018",
          title: "Frontend Developer",
          organization: "WebCraft Studios",
          description:
            "Created responsive user interfaces, collaborated with designers, and optimized website performance.",
        },
        {
          period: "2014 - 2016",
          title: "Bachelor of Science in Computer Science",
          organization: "University of Technology",
          description:
            "Graduated with honors. Specialized in web technologies and software engineering.",
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
