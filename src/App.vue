<template>
  <NavBar />
  <main>
    <HomeSection />
    <AboutSection />
    <SkillsSection />
    <PortfolioSection />
    <ContactSection />
  </main>
  <footer class="footer text-center py-3 text-muted">
    &copy; 2025 github.com/raykgomotsomongwe. All rights reserved.
  </footer>
</template>

<script setup>
import NavBar from './components/NavBar.vue'
import HomeSection from './components/HomeSection.vue'
import AboutSection from './components/AboutSection.vue'
import SkillsSection from './components/SkillSection.vue'
import PortfolioSection from './components/PortfolioSection.vue'
import ContactSection from './components/ContactSection.vue'
</script>

<style>
html {
  scroll-padding-top: 4.375rem;
  font-size: clamp(14px, 1.1vw, 18px);
}

body {
  color: #ffffff;
  background: #110f0f;
}
.headings {
  font-family: "Fredoka", sans-serif;
  font-weight: 500;
  font-size: 3rem;
}
section {
  min-height: 90vh;
  height: auto;
  scroll-snap-align: start;
  scroll-snap-stop: always;
}
@media (max-width: 48rem) {
  .navbar {
    margin: 0.625rem 1.25rem;
    flex-wrap: wrap;
    gap: 0.625rem;
    padding: 0.5rem 0.75rem;
  }
  .navbar a {
    padding: 0.375rem 0.625rem;
    font-size: 0.875rem;
  }
  #home {
    flex-direction: column;
    margin: 5rem 1.25rem;
  }
  .home {
    margin: 0 auto;
    padding: 0 0.9375rem;
  }
  #home-p {
    font-size: 3rem;
    text-align: center;
  }
  section {
    flex-direction: column;
    padding: 1.25rem;
  }
  #about {
    padding: 2.5rem 0.9375rem;
  }
  .about-wrapper {
    flex-direction: column;
    gap: 1.25rem;
  }
  .about-image {
    width: 100%;
    max-width: 18.75rem;
    margin: 0 auto;
  }
  .about-content h1 {
    font-size: 2rem;
    text-align: center;
  }
  .about-text {
    font-size: 0.9rem;
    text-align: center;
  }
  #skills {
    padding: 2.5rem 0.9375rem;
  }
  .tech-icons-wrapper {
    justify-content: center;
    gap: 1.25rem;
  }
  .box-icon {
    width: 6.25rem;
    margin-bottom: 1.25rem;
  }
  .box-icon i {
    font-size: 2.5rem;
  }
  .box-icon p {
    font-size: 0.875rem;
  }
  #portfolio {
    padding: 2.5rem 0.9375rem;
  }
  .projects-wrapper {
    gap: 2.5rem;
  }
  .project-card {
    flex-direction: column !important;
    gap: 1.875rem;
    max-width: 100%;
  }
  .project-image {
    max-width: 100%;
  }
  .project-content {
    max-width: 100%;
  }
  .project-title {
    font-size: 1.8rem;
    text-align: center;
  }
  .project-description {
    font-size: 1rem;
    text-align: center;
  }
  .project-buttons {
    justify-content: center;
  }
  #contact {
    padding: 2.5rem 0.9375rem;
  }
  .contact-container {
    flex-direction: column;
    width: 100%;
  }
  .contact-info {
    width: 100%;
    padding: 1.25rem;
    width: 100%;           
    text-align: center;
  }
  .contact-form {
    padding: 1.25rem;
    text-align: center;
  }
  .contact-form h2,
  .contact-form p {
    text-align: center;
  }
  .contact-form button {
    width: 100%;
  }
  .social-icons a {
    font-size: 2.25rem;
    margin: 0 0.375rem;
  }
}

.footer {
  text-align: center;
  padding: 1rem 0;
  color: #000;
  max-width: 25rem;
  margin: 1em auto;
  font-size: 0.9rem;
} 
</style>