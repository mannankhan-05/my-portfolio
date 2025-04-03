<template>
  <section class="section" id="skills">
    <div class="container">
      <h2 class="section-title">My Skills</h2>
      <div class="skills-content">
        <div
          class="skills-category"
          v-for="(category, index) in skills"
          :key="index"
        >
          <h3 class="category-title">{{ category.category }}</h3>
          <div class="skills-grid">
            <div
              class="skill-item"
              v-for="skill in category.items"
              :key="skill.name"
            >
              <div class="skill-icon">
                <i :class="skill.icon"></i>
              </div>
              <div class="skill-info">
                <h4 class="skill-name">{{ skill.name }}</h4>
                <div class="skill-level">
                  <div class="level-bar">
                    <div
                      class="level-fill"
                      :style="{ width: `${skill.level}%` }"
                    ></div>
                  </div>
                  <span class="level-text">{{ skill.level }}%</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "SkillsSection",
  data() {
    return {
      skills: [
        {
          category: "Frontend",
          items: [
            { name: "HTML/CSS", level: 95, icon: "fab fa-html5" },
            { name: "JavaScript", level: 90, icon: "fab fa-js" },
            { name: "Vue.js", level: 90, icon: "fab fa-vuejs" },
            { name: "SASS/SCSS", level: 85, icon: "fab fa-sass" },
          ],
        },
        {
          category: "Backend",
          items: [
            { name: "Node.js", level: 90, icon: "fab fa-node-js" },
            { name: "Express", level: 90, icon: "fas fa-server" },
            { name: "Java", level: 70, icon: "fab fa-java" },
          ],
        },
        {
          category: "Database & DevOps",
          items: [
            { name: "PostgreSQL", level: 90, icon: "fas fa-database" },
            { name: "MySQL", level: 80, icon: "fas fa-database" },
            { name: "MongoDB", level: 75, icon: "fas fa-database" },
            { name: "Docker", level: 70, icon: "fab fa-docker" },
            { name: "AWS", level: 85, icon: "fab fa-aws" },
            { name: "Git", level: 85, icon: "fab fa-git-alt" },
          ],
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

.skills-content {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 40px;
}

.category-title {
  font-size: 1.5rem;
  margin-bottom: 25px;
  position: relative;
  display: inline-block;
}

.category-title::after {
  content: "";
  position: absolute;
  bottom: -8px;
  left: 0;
  width: 40px;
  height: 3px;
  background-color: var(--accent-color);
}

.skills-grid {
  display: grid;
  gap: 20px;
}

.skill-item {
  display: flex;
  align-items: center;
  gap: 15px;
}

.skill-icon {
  width: 40px;
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: var(--icon-background);
  border-radius: 8px;
  font-size: 1.2rem;
  border: 1px solid var(--border-color);
  color: #222;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.skill-info {
  flex: 1;
}

.skill-name {
  font-size: 1rem;
  margin-bottom: 5px;
}

.skill-level {
  display: flex;
  align-items: center;
  gap: 10px;
}

.level-bar {
  flex: 1;
  height: 8px;
  background-color: #e0e0e0;
  border-radius: 4px;
  overflow: hidden;
  border: 1px solid var(--border-color);
}

.level-fill {
  height: 100%;
  background-color: var(--accent-color);
  border-radius: 4px;
}

.level-text {
  font-size: 0.8rem;
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

  .skills-content {
    grid-template-columns: 1fr;
  }
}
</style>
