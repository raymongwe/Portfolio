<template>
  <section id="portfolio">
    <div class="portfolio headings d-flex justify-content-center">
      <p>Portfolio</p>
    </div>
    <div class="heading d-flex justify-content-center">
      <p>a selection of things i've built</p>
    </div>
    <br>

    <div class="projects-wrapper">
      <div
        v-for="(project, index) in projects"
        :key="project.title"
        class="project-card"
        :class="index % 2 === 0 ? 'card-left' : 'card-right'"
      >
        <div class="project-image">
          <img :src="project.image" :alt="project.title" class="project-screenshot">
        </div>
        <div class="project-content">
          <h2 class="project-title">{{ project.title }}</h2>
          <p class="project-tagline">{{ project.tagline }}</p>

          <div class="project-tech">
            <i
              v-for="tech in project.tech"
              :key="tech.name"
              :class="tech.icon.split(' ')"
              :title="tech.name"
            ></i>
          </div>

          <div class="project-buttons">
            <a :href="project.liveUrl" class="project-button primary" target="_blank" rel="noopener noreferrer">Live Demo</a>
            <button
              @click="project.expanded = !project.expanded"
              class="project-button secondary"
            >
              {{ project.expanded ? 'Read Less' : 'Read More' }}
            </button>
          </div>

          <Transition name="slide-fade">
            <div v-if="project.expanded" class="project-details">
              <p>{{ project.details }}</p>
            </div>
          </Transition>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { reactive } from 'vue'
import { projects as projectData } from '../data/projects.js'

// Ensure each project has an 'expanded' property
const projects = reactive(projectData.map(p => ({ ...p, expanded: false })))
</script>

<style scoped>
#portfolio {
  max-width: 62.5rem;
  margin: 0 auto;
  padding: 5rem 1.25rem;
  font-family: "Poppins", sans-serif;
}

.projects-wrapper {
  display: flex;
  flex-direction: column;
  gap: 5rem;
}

.project-card {
  display: flex;
  gap: 3.75rem;
  align-items: center;
  max-width: 62.5rem;
  margin: 0 auto;
}

.card-left { flex-direction: row; }
.card-right { flex-direction: row-reverse; }

.project-image {
  flex: 1.2;
  max-width: 43.75rem;
  border-radius: 1.25rem;
  box-shadow: 0 0.625rem 9rem rgba(13, 202, 240, 0.4);
}

.project-screenshot {
  width: 100%;
  height: auto;
  box-shadow: 0 0.375rem 1.875rem rgba(0, 0, 0, 0.15);
  border: none;
  border-radius: 0.5rem;
}

.project-content {
  flex: 1.8;
  max-width: 31.25rem;
}

.project-title {
  font-size: 2.4rem;
  font-weight: 700;
  margin-bottom: 0.5rem;
  color: #fff;
}

.project-tagline {
  font-size: 1rem;
  color: rgba(255, 255, 255, 0.7);
  margin-bottom: 1rem;
  font-style: italic;
}

.project-tech {
  display: flex;
  gap: 0.75rem;
  margin-bottom: 1.5rem;
  flex-wrap: wrap;
}

.project-tech i {
  font-size: 1.8rem;
  width: 1.8rem;
  height: 1.8rem;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: transform 0.2s ease;
}

.project-tech i:hover { transform: scale(1.2); }

.project-buttons {
  display: flex;
  gap: 1.5rem;
}

.project-button {
  padding: 1rem 2rem;
  border-radius: 0.5rem;
  font-weight: 600;
  text-decoration: none;
  transition: all 0.25s ease;
  cursor: pointer;
  font-size: 1.1rem;
  border: none;
}

.primary {
  background-color: #17707e;
  color: white;
  transition: background-color 0.8s, color 0.8s, transform 0.2s ease;
}

.secondary {
  background-color: #f0f0f0;
  color: #333;
  border: 1px solid gray;
  transition: background-color 0.8s, color 0.8s, transform 0.2s ease;
}

.primary:hover {
  background-color: gray;
  transform: scale(1.1) translateY(-0.0625rem);
}

.secondary:hover {
  background-color: gray;
  color: #fff;
  transform: scale(1.1) translateY(-0.0625rem);
}

.project-details {
  margin-top: 1.5rem;
  padding: 1.25rem;
  background-color: rgba(255, 255, 255, 0.08);
  border-left: 3px solid #17707e;
  border-radius: 0.5rem;
  font-size: 1rem;
  line-height: 1.8;
  color: #fff;
}

/* --- SMOOTH OPEN/CLOSE TRANSITIONS --- */

/* This handles the "In" and "Out" timing */
.slide-fade-enter-active {
  transition: all 0.4s ease-out;
}

.slide-fade-leave-active {
  transition: all 0.3s ease-in;
}

/* This is the state when it is hidden (Both before opening and after closing) */
.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateY(-0.625rem);
  opacity: 0;
}
</style>