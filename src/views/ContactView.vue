<template>
  <div class="contact">
    <section class="hero">
      <div class="hero-content">
        <div class="hero-text">
          <h1>Contact</h1>
          <p class="hero-subtitle">Let’s build something great together.</p>
        </div>
      </div>
    </section>

    <section class="content">
      <div class="container">
        <div class="intro">
          <h2>Get In Touch</h2>
          <p>Feel free to reach out for collaborations, opportunities, or just to say hello.</p>
        </div>

        <form class="contact-form" @submit.prevent="submitForm">
          <div class="form-grid">
            <div class="form-group">
              <label for="name">Name</label>
              <input v-model.trim="form.name" id="name" type="text" required />
            </div>
            <div class="form-group">
              <label for="email">Email</label>
              <input v-model.trim="form.email" id="email" type="email" required />
            </div>
            <div class="form-group full">
              <label for="subject">Subject</label>
              <input v-model.trim="form.subject" id="subject" type="text" required />
            </div>
            <div class="form-group full">
              <label for="message">Message</label>
              <textarea v-model.trim="form.message" id="message" rows="6" required></textarea>
            </div>
          </div>

          <div class="actions">
            <button :disabled="submitting" :class="{ 'is-loading': submitting }">
              <span class="btn-label" v-if="!submitting">Send Message</span>
              <span class="btn-label" v-else>Sending...</span>
            </button>
            <p v-if="success" class="status success">Message sent successfully.</p>
            <p v-if="error" class="status error">{{ error }}</p>
          </div>
        </form>

        <div class="other-links">
          <h3>Other Channels</h3>
          <ul>
            <li><a href="mailto:you@example.com">you@example.com</a></li>
            <li>
              <a href="https://github.com/yourhandle" target="_blank" rel="noopener">GitHub</a>
            </li>
            <li>
              <a href="https://www.linkedin.com/in/yourhandle" target="_blank" rel="noopener"
                >LinkedIn</a
              >
            </li>
          </ul>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup lang="ts">
import { reactive, ref } from 'vue'

interface ContactForm {
  name: string
  email: string
  subject: string
  message: string
}

const form = reactive<ContactForm>({
  name: '',
  email: '',
  subject: '',
  message: '',
})

const submitting = ref(false)
const success = ref(false)
const error = ref('')

function reset() {
  form.name = ''
  form.email = ''
  form.subject = ''
  form.message = ''
}

async function submitForm() {
  error.value = ''
  success.value = false
  submitting.value = true
  try {
    await new Promise((r) => setTimeout(r, 900))
    success.value = true
    reset()
  } catch (e) {
    error.value = 'Failed to send. Please try again.'
  } finally {
    submitting.value = false
  }
}
</script>

<style scoped>
.contact {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

.hero {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: #fff;
  padding: clamp(3.5rem, 8vw, 5rem) 0 3rem;
  margin-top: -1rem;
  position: relative;
  overflow: hidden;
}

.hero::after {
  content: '';
  position: absolute;
  inset: 0;
  background:
    radial-gradient(circle at 20% 30%, rgba(255, 255, 255, 0.15), transparent 60%),
    radial-gradient(circle at 80% 70%, rgba(255, 255, 255, 0.12), transparent 65%);
  pointer-events: none;
}

.hero-content {
  max-width: 1100px;
  margin: 0 auto;
  padding: 0 clamp(1rem, 3vw, 2rem);
}

.hero h1 {
  font-size: clamp(2.25rem, 5vw, 3.25rem);
  margin-bottom: 0.75rem;
  font-weight: 700;
  letter-spacing: -0.5px;
}

.hero-subtitle {
  font-size: clamp(1.05rem, 1.6vw, 1.3rem);
  opacity: 0.92;
  line-height: 1.55;
  max-width: 52ch;
}

.content {
  padding: clamp(2.5rem, 6vw, 4rem) 0;
  flex: 1;
}

.container {
  max-width: 920px;
  margin: 0 auto;
  padding: 0 clamp(1rem, 3vw, 2rem);
}

.intro {
  margin-bottom: clamp(1.75rem, 4vw, 2.75rem);
}

.intro h2 {
  font-size: clamp(1.9rem, 4vw, 2.4rem);
  margin-bottom: 0.85rem;
  color: var(--color-text);
  line-height: 1.15;
}

.intro p {
  color: var(--color-text);
  line-height: 1.65;
  font-size: 1.05rem;
  max-width: 70ch;
}

.contact-form {
  background: linear-gradient(var(--color-background-soft), var(--color-background-soft))
    padding-box;
  backdrop-filter: blur(6px);
  -webkit-backdrop-filter: blur(6px);
  padding: clamp(1.5rem, 3vw, 2.25rem);
  border: 1px solid var(--color-border);
  border-radius: 18px;
  margin-bottom: 3.25rem;
  position: relative;
  box-shadow: 0 4px 18px -6px rgba(0, 0, 0, 0.12);
}

.contact-form:focus-within {
  border-color: #6f72ff;
  box-shadow: 0 0 0 3px rgba(111, 114, 255, 0.25);
  transition: box-shadow 0.3s;
}

.form-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(min(240px, 100%), 1fr));
  gap: 1.3rem 1.6rem;
}

.full {
  grid-column: 1 / -1;
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 0.55rem;
}

label {
  font-weight: 600;
  font-size: 0.8rem;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  color: var(--color-text);
  opacity: 0.85;
}

input,
textarea {
  border: 1px solid var(--color-border);
  background: var(--color-background);
  padding: 0.85rem 0.95rem;
  border-radius: 10px;
  font: inherit;
  color: var(--color-text);
  resize: vertical;
  line-height: 1.4;
  transition:
    border-color 0.18s,
    box-shadow 0.18s,
    background 0.25s;
}

input:hover,
textarea:hover {
  border-color: #667eea;
}

input:focus-visible,
textarea:focus-visible {
  outline: 0;
  border-color: #667eea;
  box-shadow: 0 0 0 3px color-mix(in srgb, #667eea 55%, transparent);
}

::placeholder {
  opacity: 0.55;
}

.form-group.invalid input,
.form-group.invalid textarea {
  border-color: #e53e3e;
  box-shadow: 0 0 0 2px rgba(229, 62, 62, 0.25);
}

.form-group.invalid label {
  color: #e53e3e;
}

button {
  --btn-bg: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  background: var(--btn-bg);
  color: #fff;
  font-weight: 600;
  padding: 0.95rem 2.15rem;
  border: 0;
  border-radius: 40px;
  cursor: pointer;
  font-size: 0.95rem;
  line-height: 1;
  display: inline-flex;
  align-items: center;
  gap: 0.6rem;
  position: relative;
  isolation: isolate;
  transition:
    background 0.25s,
    transform 0.25s,
    box-shadow 0.25s;
}

button::after {
  content: '';
  position: absolute;
  inset: 0;
  border-radius: inherit;
  background: linear-gradient(135deg, #7b8ff6 0%, #8a65c2 100%);
  opacity: 0;
  z-index: -1;
  transition: opacity 0.35s;
}

@media (hover: hover) {
  button:hover:not(:disabled) {
    transform: translateY(-3px);
    box-shadow: 0 10px 25px -8px rgba(102, 126, 234, 0.5);
  }
  button:hover:not(:disabled)::after {
    opacity: 1;
  }
}

button:active:not(:disabled) {
  transform: translateY(-1px);
}

button:disabled {
  opacity: 0.55;
  cursor: not-allowed;
  box-shadow: none;
  transform: none;
}

button.is-loading {
  padding-right: 2.8rem;
}

button.is-loading .btn-label {
  opacity: 0.85;
}

button.is-loading::before {
  content: '';
  position: absolute;
  right: 1.1rem;
  width: 1.05rem;
  height: 1.05rem;
  border: 2px solid rgba(255, 255, 255, 0.55);
  border-top-color: #fff;
  border-radius: 50%;
  animation: spin 0.8s linear infinite;
}

@keyframes spin {
  to {
    transform: rotate(360deg);
  }
}

.actions {
  margin-top: 1.35rem;
  display: flex;
  flex-direction: column;
  gap: 0.85rem;
}

.status {
  font-size: 0.8rem;
  letter-spacing: 0.02em;
}

.status.success {
  color: #2f855a;
}

.status.error {
  color: #c53030;
}

.other-links h3 {
  font-size: clamp(1.25rem, 2.2vw, 1.6rem);
  margin-bottom: 1rem;
  color: var(--color-text);
}

.other-links ul {
  list-style: none;
  padding: 0;
  margin: 0;
  display: grid;
  gap: 0.6rem;
}

.other-links a {
  color: #667eea;
  text-decoration: none;
  font-weight: 500;
  position: relative;
  padding-bottom: 2px;
}

.other-links a::after {
  content: '';
  position: absolute;
  left: 0;
  bottom: 0;
  height: 2px;
  width: 0;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  transition: width 0.35s;
}

.other-links a:focus-visible {
  outline: 0;
  box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.4);
  border-radius: 4px;
}

.other-links a:hover::after,
.other-links a:focus-visible::after {
  width: 100%;
}

@media (max-width: 640px) {
  .contact-form {
    padding: 1.4rem 1.25rem 1.7rem;
  }
  button {
    width: 100%;
    justify-content: center;
  }
}

@media (prefers-reduced-motion: reduce) {
  * {
    animation: none !important;
    transition: none !important;
  }
}

/* Dark mode adjustments (if variables not already handling) */
@media (prefers-color-scheme: dark) {
  .contact-form {
    box-shadow: 0 4px 18px -6px rgba(0, 0, 0, 0.6);
  }
  input,
  textarea {
    background: color-mix(in srgb, var(--color-background) 92%, #222);
  }
  button {
    box-shadow: 0 6px 18px -6px rgba(102, 126, 234, 0.45);
  }
  button:hover:not(:disabled) {
    box-shadow: 0 10px 28px -8px rgba(102, 126, 234, 0.55);
  }
}
</style>
