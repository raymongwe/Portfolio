<template>
  <nav class="navbar navbar-expand-lg" :class="{ 'scrolled': isScrolled }">
    <div class="container-fluid">
      <div class="burger" @click="isMenuOpen = !isMenuOpen">
        <span :class="{ 'line-top': isMenuOpen }"></span>
        <span :class="{ 'line-mid': isMenuOpen }"></span>
        <span :class="{ 'line-bot': isMenuOpen }"></span>
      </div>

      <ul class="navbar-nav ms-auto" :class="{ 'nav-active': isMenuOpen }">
        <li
          v-for="link in navLinks"
          :key="link.label"
          class="nav-item mx-3"
        >
          <a class="nav-link text-white" :href="link.href" @click="isMenuOpen = false">
            {{ link.label }}
          </a>
        </li>
      </ul>
    </div>
  </nav>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

const isMenuOpen = ref(false);
const isScrolled = ref(false);
let observer = null;

const navLinks = [
  { label: 'Home', href: '#home' },
  { label: 'About', href: '#about' },
  { label: 'Skills', href: '#skills' },
  { label: 'Portfolio', href: '#portfolio' },
  { label: 'Contact', href: '#contact' },
];

onMounted(() => {
  const homeSection = document.querySelector('#home');
  
  if (homeSection) {
    const options = {
      threshold: 0.1, // Trigger when only 10% of #home is visible
      rootMargin: "-100px 0px 0px 0px" // Adjusted for navbar height
    };

    observer = new IntersectionObserver(([entry]) => {
      // If home is NOT intersecting, it means we've scrolled past it
      isScrolled.value = !entry.isIntersecting;
    }, options);

    observer.observe(homeSection);
  }
});

onUnmounted(() => {
  if (observer) observer.disconnect();
});
</script>

<style scoped>
.navbar {
  position: fixed;
  top: 3%;
  right: 0;
  width: 100%;
  padding: 0.625rem 1.25rem;
  display: flex;
  z-index: 100;
  background-color: transparent;
  transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
}

.navbar.scrolled {
  top: 0;
  padding: 0.8rem 1.25rem;
  background-color: #110f0f;
  backdrop-filter: blur(12px);
}

.navbar a {
  text-decoration: none;
  padding: 0.5rem 0.75rem;
  transition: all 0.3s ease;
}

.navbar a:hover {
  border-radius: 0.625rem;
  color: gray !important;
}

.burger {
  display: flex;
  flex-direction: column;
  gap: 6px;
  cursor: pointer;
  z-index: 101;
  margin-left: auto;
}

.burger span {
  display: block;
  width: 30px;
  height: 2px;
  background-color: #ffffff;
  box-shadow: 0 0 10px rgba(146, 225, 226, 0.5);
  transition: all 0.3s ease-in-out;
}

/* Burger Animation */
.line-top { transform: translateY(8px) rotate(45deg); }
.line-mid { opacity: 0; }
.line-bot { transform: translateY(-8px) rotate(-45deg); }

@media (max-width: 991px) {
  .nav-link {
    font-size: 2rem;
    font-weight: 600;
    letter-spacing: 2px;
    text-transform: uppercase;
    padding: 1.5rem 0 !important;
    width: 100%;
    text-align: center;
  }
  .navbar-nav {
    position: fixed;
    right: -100%;
    top: 0;
    flex-direction: column;
    background: rgba(10, 15, 23, 0.98);
    backdrop-filter: blur(15px);
    width: 70%;
    height: 100vh;
    justify-content: center;
    align-items: center;
    transition: right 0.4s ease-in-out;
    border-left: 1px solid rgba(146, 225, 226, 0.3);
    margin: 0 !important;
  }

  .nav-active {
    right: 0 !important;
  }
}

@media (min-width: 992px) {
  .burger {
    display: none;
  }
}
</style>