<template>
  <section id="contact">
    <div class="contact-headings">
      <p>Contact me</p>
    </div>

    <div class="contact-container">
      <div class="contact-info">
        <p><i class="icon fa-solid fa-envelope"></i>
          <a href="mailto:raykgomotsomongwe@gmail.com" target="_blank">raykgomotsomongwe</a>
        </p>
        <p><i class="icon fa-solid fa-phone"></i> +27 63 654 1663</p>
        <p><i class="icon fab fa-github"></i>
          <a href="https://github.com/RayKgomotsoMongwe" target="_blank">github</a>
        </p>
        <p><i class="icon fab fa-linkedin"></i>
          <a href="https://linkedin.com/in/ray-junior-kgomotso-mongwe" target="_blank">linkedin</a>
        </p>
      </div>

      <div class="contact-form">
        <h2>Get in Touch</h2>
        <p>Feel free to drop a line below!</p>

        <input v-model="formData.name" type="text" placeholder="Your Name" required />
        <input v-model="formData.email" type="email" placeholder="Your Email" required />
        <textarea v-model="formData.message" placeholder="Type your message here..." required></textarea>

        <button @click="handleSubmit">Send</button>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const formData = ref({
  name: '',
  email: '',
  message: ''
})

const handleSubmit = () => {
  const form = document.createElement('form')
  form.method = 'POST'
  form.action = 'https://formsubmit.co/raykgomotsomongwe@gmail.com'

  const fields = {
    name: formData.value.name,
    email: formData.value.email,
    message: formData.value.message
  }

  Object.entries(fields).forEach(([key, value]) => {
    const input = document.createElement('input')
    input.type = 'hidden'
    input.name = key
    input.value = value
    form.appendChild(input)
  })

  document.body.appendChild(form)
  form.submit()
}
</script>

<style scoped>
#contact {
  max-width: 62.5rem;
  margin: 0 auto;
  padding: 5rem 1.25rem;
  font-family: "Poppins", sans-serif;
  display: flex;
  flex-direction: column; 
  align-items: center;    
  gap: 3rem;              
}

.contact-headings p {
  font-size: 3.5rem;
  font-weight: bold;
  color: white;
  margin: 0;
  text-align: center;
}

.contact-container {
  display: flex;
  flex-direction: row;
  background: #110f0f;
  overflow: hidden;
  border-radius: 1.25rem;
  box-shadow: 0 0.625rem 9rem rgba(13,202,240,0.4);
  width: 100%;
}

.contact-info {
  background-color: #131314;
  color: #fff;
  padding: 2.5rem 1.875rem;
  width: 18.75rem;
  flex-shrink: 0;
}

.contact-info p {
  margin: 0.9375rem 0;
  line-height: 1.6;
}

.contact-info p:hover,
.contact-info a:hover {
  transition: background-color 0.8s,color 0.8s, transform 0.2s ease;
  color: gray;
}

.contact-info a {
  color: #fff;
  text-decoration: none;
}

.contact-form {
  padding: 2.5rem 1.875rem;
  flex: 1;
}

.contact-form h2 {
  color: #fff;
  margin-bottom: 0.625rem;
}

.contact-form p {
  color: #a8a8a8;
  margin-bottom: 1.25rem;
}

.contact-form input,
.contact-form textarea {
  width: 100%;
  padding: 0.75rem;
  margin-bottom: 0.9375rem;
  border: none;
  background-color: #f2f2f2;
  border-radius: 0.3125rem;
  box-sizing: border-box; 
}

.contact-form textarea {
  height: 6.25rem;
  resize: none;
}

.contact-form button {
  background-color: #17707e;
  color: #fff;
  padding: 0.75rem 1.875rem;
  border: none;
  border-radius: 1.5625rem;
  cursor: pointer;
  font-weight: bold;
  transition: background-color 0.8s,color 0.8s, transform 0.2s ease;
}

.contact-form button:hover {
  background-color: gray;
  transform: scale(1.1) translateY(-0.0625rem);
}

/* --- MOBILE REACTIVITY --- */
@media (max-width: 48rem) {
  #contact {
    padding: 2.5rem 1rem;
  }

  .contact-headings p {
    font-size: 2.5rem;
  }

  .contact-container {
    flex-direction: column; 
  }

  .contact-info {
    width: 100%;
    padding: 2rem 1rem;
    text-align: center;
  }

  .contact-form {
    padding: 2rem 1.25rem;
    text-align: center;
  }

  .contact-form button {
    width: 100%;
  }
}
</style>