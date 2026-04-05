<template>
  <section id="home">
    <div id="particles-js"></div>

    <div class="home">
      <p id="home-p">
        {{ displayText }}<span :class="{ 'cursor': true, 'typing-active': !typingComplete }">|</span>
      </p>

      <div class="after-typing">
        <TransitionGroup name="staggered-pop" tag="div" class="social-icons">
          <a v-if="typingComplete" 
             v-for="(link, index) in socialLinks" 
             :key="link.icon"
             :href="link.url" 
             target="_blank"
             :style="{ transitionDelay: `${index * 0.15}s` }">
            <i :class="link.icon"></i>
          </a>
        </TransitionGroup>
        
        <Transition name="slide-fade">
          <div v-if="typingComplete" class="home-p2">
            <p>
              I love creating, solving problems, <br />
              and — admittedly — might have an unhealthy obsession with cycling 🚲
            </p>
          </div>
        </Transition>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'

// --- Typing Logic State ---
const fullText = "Hello, I'm Ray | Software Engineer";
const displayText = ref('');
const typingComplete = ref(false);

const socialLinks = [
  { icon: 'fas fa-envelope', url: 'mailto:raykgomotsomongwe@gmail.com' },
  { icon: 'fab fa-linkedin', url: 'https://linkedin.com/in/ray-junior-kgomotso-mongwe' },
  { icon: 'fab fa-github', url: 'https://github.com/RayKgomotsoMongwe' }
];

const typeText = () => {
  let i = 0;
  const speed = 60; // ms per character

  const timer = setInterval(() => {
    if (i < fullText.length) {
      displayText.value += fullText.charAt(i);
      i++;
    } else {
      clearInterval(timer);
      // Half-second pause before popping the rest of the UI
      setTimeout(() => {
        typingComplete.value = true;
      }, 500);
    }
  }, speed);
};

onMounted(() => {
  typeText();

  // --- Particles.js Configuration ---
  if (window.particlesJS) {
    window.particlesJS("particles-js", {
      particles: {
        number: { value: 60, density: { enable: true, value_area: 800 } },
        color: { value: "#ffffff" },
        shape: { type: "circle" },
        opacity: { value: 0.5 },
        size: { value: 4, random: true },
        line_linked: {
          enable: true,
          distance: 150,
          color: "#ffffff",
          opacity: 0.3,
          width: 1
        },
        move: { enable: true, speed: 3 }
      },
      interactivity: {
        detect_on: "canvas",
        events: {
          onhover: { enable: true, mode: "repulse" },
          onclick: { enable: true, mode: "push" },
          resize: true
        },
        modes: {
          repulse: { distance: 100, duration: 0.4 },
          push: { quantity: 4 }
        }
      },
      retina_detect: true
    });
  }
});
</script>

<style scoped>
#home {
  position: relative;
  overflow: hidden;
  color: #ffffff;
  min-height: 100vh;
  display: flex;
  align-items: center;
  background-color: #110f0f; 
}

#particles-js {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 0;
}

.home {
  margin: 0 9.375rem;
  position: relative;
  z-index: 2;
  pointer-events: none;
}

.social-icons a {
  pointer-events: auto;
}

#home-p {
  font-family: "Fredoka", sans-serif;
  font-weight: 700;
  font-size: 5rem;
  margin-bottom: 1rem;
  line-height: 1.2;
  min-height: 12rem; 
  user-select: none;
}

/* --- Typing Cursor --- */
.cursor {
  display: inline-block;
  color: #34d4ec;
  margin-left: 5px;
  animation: blink 0.8s infinite;
}

@keyframes blink {
  0%, 100% { opacity: 1; }
  50% { opacity: 0; }
}

.social-icons {
  display: flex;
  gap: 1.5rem;
  pointer-events: auto;
}

.social-icons a {
  display: inline-block;
  color: #34d4ec;
  text-decoration: none;
  font-size: 2.8125rem;
  transition: color 0.8s, transform 0.3s ease;
}

.social-icons a:hover {
  color: gray;
  transform: scale(1.1) translateY(-0.3125rem);
}

.home-p2 {
  margin-top: 2rem;
  font-family: "Fredoka", sans-serif;
  font-weight: 400;
  font-size: 1.25rem;
  color: rgba(255, 255, 255, 0.8);
  user-select: none;
}

/* --- Vue Animations (Transitions) --- */

/* Bouncy entrance for Icons */
.staggered-pop-enter-active {
  transition: all 0.5s cubic-bezier(0.34, 1.56, 0.64, 1);
}
.staggered-pop-enter-from {
  opacity: 0;
  transform: scale(0.5) translateY(20px);
}

/* Slide and Fade for sub-text */
.slide-fade-enter-active {
  transition: all 0.8s ease-out;
  transition-delay: 0.6s; /* Starts after icons finish popping */
}
.slide-fade-enter-from {
  opacity: 0;
  transform: translateX(-30px);
}

@media (max-width: 768px) {
  .home { margin: 2rem; }
  #home-p { font-size: 3rem; min-height: 8rem; }
  .social-icons a { font-size: 2rem; }
}
</style>