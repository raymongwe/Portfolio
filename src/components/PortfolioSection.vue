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
          <p class="project-description">{{ project.description }}</p>
          <div class="project-buttons">
            <a :href="project.liveUrl" class="project-button primary">Live Demo</a>
            <a :href="project.readMore" class="project-button secondary">Read More</a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { projects } from '../data/projects.js'
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

.card-left {
  flex-direction: row;
}

.card-right {
  flex-direction: row-reverse;
}

.project-image {
  flex: 1.2;
  max-width: 43.75rem;
  border-radius: 1.25rem;
  box-shadow: 0 0.625rem 9rem rgba(13,202,240,0.4);
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
  margin-bottom: 1.2rem;
  color: #fff;
}

.project-description {
  font-size: 1.3rem;
  line-height: 1.8;
  color: #fff;
  margin-bottom: 2.5rem;
}

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
}

.primary {
  background-color: #17707e;
  color: white;
  transition: background-color 0.8s,color 0.8s, transform 0.2s ease;
}

.secondary {
  background-color: #f0f0f0;
  color: #333;
  border: 1px solid gray;
  transition: background-color 0.8s,color 0.8s, transform 0.2s ease;
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
</style>