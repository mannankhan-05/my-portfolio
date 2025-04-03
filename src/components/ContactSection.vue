<template>
  <section class="section" id="contact">
    <div class="container">
      <h2 class="section-title">Get In Touch</h2>
      <div class="contact-content">
        <div class="contact-info">
          <h3 class="contact-subtitle">Contact Information</h3>
          <p class="contact-text">
            Feel free to reach out to me for collaboration or opportunities. I'm
            always open to discussing new projects, creative ideas, or
            opportunities to be part of your vision.
          </p>
          <div class="contact-details">
            <div class="contact-item">
              <div class="contact-icon">
                <i class="fas fa-map-marker-alt"></i>
              </div>
              <div class="contact-text">
                <h4>Location</h4>
                <p>San Francisco, CA</p>
              </div>
            </div>
            <div class="contact-item">
              <div class="contact-icon">
                <i class="fas fa-envelope"></i>
              </div>
              <div class="contact-text">
                <h4>Email</h4>
                <p>john@example.com</p>
              </div>
            </div>
            <div class="contact-item">
              <div class="contact-icon">
                <i class="fas fa-phone-alt"></i>
              </div>
              <div class="contact-text">
                <h4>Phone</h4>
                <p>+1 (123) 456-7890</p>
              </div>
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
          </div>
        </div>
        <div class="contact-form">
          <h3 class="contact-subtitle">Send Me a Message</h3>
          <form @submit.prevent="submitForm">
            <div class="form-group">
              <label for="name">Name</label>
              <input type="text" id="name" v-model="form.name" required />
            </div>
            <div class="form-group">
              <label for="email">Email</label>
              <input type="email" id="email" v-model="form.email" required />
            </div>
            <div class="form-group">
              <label for="subject">Subject</label>
              <input type="text" id="subject" v-model="form.subject" required />
            </div>
            <div class="form-group">
              <label for="message">Message</label>
              <textarea
                id="message"
                v-model="form.message"
                rows="5"
                required
              ></textarea>
            </div>
            <button
              type="submit"
              class="btn btn-primary"
              :disabled="isSubmitting"
            >
              <span v-if="isSubmitting">Sending...</span>
              <span v-else>Send Message</span>
            </button>
          </form>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "ContactSection",
  data() {
    return {
      isSubmitting: false,
      form: {
        name: "",
        email: "",
        subject: "",
        message: "",
      },
    };
  },
  methods: {
    async submitForm() {
      this.isSubmitting = true;

      // Simulate form submission
      await new Promise((resolve) => setTimeout(resolve, 2000));

      // Reset form
      this.form = {
        name: "",
        email: "",
        subject: "",
        message: "",
      };

      this.isSubmitting = false;
      alert("Your message has been sent successfully!");
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

.contact-content {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 50px;
}

.contact-subtitle {
  font-size: 1.5rem;
  margin-bottom: 20px;
}

.contact-text {
  color: var(--secondary-color);
  margin-bottom: 30px;
}

.contact-details {
  display: flex;
  flex-direction: column;
  gap: 20px;
  margin-bottom: 30px;
}

.contact-item {
  display: flex;
  align-items: flex-start;
  gap: 15px;
}

.contact-icon {
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

.contact-text h4 {
  font-size: 1rem;
  margin-bottom: 5px;
}

.contact-text p {
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

.form-group {
  margin-bottom: 20px;
}

.form-group label {
  display: block;
  margin-bottom: 8px;
  font-weight: 500;
}

.form-group input,
.form-group textarea {
  width: 100%;
  padding: 12px;
  border: 2px solid var(--form-border-color);
  border-radius: 4px;
  background-color: var(--background-color);
  color: var(--text-color);
  transition: all 0.3s ease;
  box-shadow: inset 0 1px 3px rgba(0, 0, 0, 0.1);
}

.form-group input:focus,
.form-group textarea:focus {
  outline: none;
  border-color: var(--accent-color);
}

@media (max-width: 768px) {
  .section {
    padding: 70px 0;
  }

  .section-title {
    font-size: 2rem;
    margin-bottom: 40px;
  }

  .contact-content {
    grid-template-columns: 1fr;
  }
}
</style>
