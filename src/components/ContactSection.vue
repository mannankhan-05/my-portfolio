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
                <p>Karachi, Pakistan</p>
              </div>
            </div>
            <div class="contact-item">
              <div class="contact-icon">
                <i class="fas fa-envelope"></i>
              </div>
              <div class="contact-text">
                <h4>Email</h4>
                <p>abdulmannan.khan005@gmail.com</p>
              </div>
            </div>
            <div class="contact-item">
              <div class="contact-icon">
                <i class="fas fa-phone-alt"></i>
              </div>
              <div class="contact-text">
                <h4>Phone</h4>
                <p>+92 323 2007068</p>
              </div>
            </div>
          </div>
          <div class="social-links">
            <a
              href="https://github.com/mannankhan-05/"
              class="social-link"
              aria-label="GitHub"
            >
              <i class="fab fa-github"></i>
            </a>
            <a
              href="https://www.linkedin.com/in/amannankhan/"
              class="social-link"
              aria-label="LinkedIn"
            >
              <i class="fab fa-linkedin"></i>
            </a>
            <a
              href="https://www.facebook.com/abdulmannan.khan.14855"
              class="social-link"
              aria-label="facebook"
            >
              <i class="fab fa-facebook"></i>
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
import emailjs from "emailjs-com";

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
      await emailjs
        .send(
          process.env.VUE_APP_EMAILJS_SERVICE_ID,
          process.env.VUE_APP_EMAILJS_TEMPLATE_ID,
          this.form,
          process.env.VUE_APP_EMAILJS_PUBLIC_KEY
        )
        .then((response) => {
          console.log("SUCCESS!", response.status, response.text);
        })
        .catch((error) => {
          console.error("FAILED...", error);
        });

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
