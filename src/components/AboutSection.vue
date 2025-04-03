<template>
  <section class="section" id="about">
    <div class="container">
      <h2 class="section-title">About Me</h2>
      <div class="about-content">
        <div class="about-image">
          <!-- Replace with your image -->
          <div class="placeholder-image"></div>
        </div>
        <div class="about-text">
          <p>
            I'm a passionate Full Stack Developer with expertise in building
            robust web applications from front to back. With a strong foundation
            in both client and server-side technologies, I enjoy creating
            seamless user experiences that solve real-world problems.
          </p>
          <p>
            My journey in software development began 5 years ago, and since
            then, I've worked on a diverse range of projects from e-commerce
            platforms to data-intensive applications. I'm constantly learning
            and adapting to new technologies to stay at the forefront of this
            ever-evolving field.
          </p>
          <div class="about-details">
            <div class="detail-item">
              <span class="detail-label">Name:</span>
              <span class="detail-value">John Doe</span>
            </div>
            <div class="detail-item">
              <span class="detail-label">Email:</span>
              <span class="detail-value">john@example.com</span>
            </div>
            <div class="detail-item">
              <span class="detail-label">Location:</span>
              <span class="detail-value">San Francisco, CA</span>
            </div>
            <div class="detail-item">
              <span class="detail-label">Availability:</span>
              <span class="detail-value">Open to opportunities</span>
            </div>
          </div>
          <div class="social-links">
            <a href="#" class="social-link" aria-label="GitHub">
              <i class="fab fa-github"></i>
            </a>
            <a href="#" class="social-link" aria-label="LinkedIn">
              <i class="fab fa-linkedin"></i>
            </a>
            <a href="#" class="social-link" aria-label="Twitter">
              <i class="fab fa-twitter"></i>
            </a>
            <a href="#" class="social-link" aria-label="Medium">
              <i class="fab fa-medium"></i>
            </a>
          </div>
          <a href="#" class="btn btn-primary">Download Resume</a>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "AboutSection",
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

.about-content {
  display: flex;
  gap: 50px;
  align-items: center;
}

.about-image {
  flex: 1;
  max-width: 400px;
  height: 500px;
  border-radius: 8px;
  overflow: hidden;
}

.placeholder-image {
  width: 100%;
  height: 100%;
  background-color: #e0e0e0;
  border-radius: 8px;
  border: 1px solid var(--border-color);
}

.about-text {
  flex: 1;
}

.about-text p {
  margin-bottom: 20px;
  color: var(--secondary-color);
}

.about-details {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 20px;
  margin: 30px 0;
}

.detail-item {
  display: flex;
  align-items: center;
}

.detail-label {
  font-weight: 600;
  margin-right: 10px;
}

.detail-value {
  color: var(--secondary-color);
}

.social-links {
  display: flex;
  gap: 15px;
  margin-bottom: 30px;
}

.social-link {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background-color: var(--icon-background);
  color: #222;
  font-size: 1.2rem;
  transition: all 0.3s ease;
  border: 1px solid var(--border-color);
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.social-link:hover {
  background-color: var(--accent-color);
  color: white;
}

@media (max-width: 992px) {
  .about-content {
    flex-direction: column;
  }

  .about-image {
    max-width: 100%;
    margin-bottom: 30px;
  }

  .about-details {
    grid-template-columns: 1fr;
  }

  .social-links {
    justify-content: center;
  }
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
</style>
