<template>
  <section id="skills">
    <div class="skills">
      <h1 class="headings row justify-content-center">Skills and Tools</h1>
      <p class="row justify-content-center" id="skills-header-text">
        The skills, tools and technologies I use to bring ideas to life.
      </p>
      <br>
      <div class="d-flex flex-wrap justify-content-start gap-4 text-center">
        <div class="tech-icons-wrapper">
          <div
            v-for="skill in skills"
            :key="skill.name"
            class="box-icon"
          >
            <!-- :class makes the class dynamic — reads from skill.icon -->
            <i :class="`devicon ${skill.icon}`"></i>
            <p class="icon-link">
              <!-- :href reads from skill.url -->
              <a :href="skill.url" target="_blank">{{ skill.name }}</a>
            </p>
          </div>

        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { skills } from '../data/skills.js'
</script>

<style scoped>
#skills {
  font-family: "Poppins", sans-serif;
  max-width: 75rem;
  margin: 0 auto;
  padding: 5rem 1.25rem;
}

.tech-icons-wrapper {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 2.5rem;
  max-width: 75rem;
  margin: 0 auto;
  padding: 1rem;
}

.box-icon {
  width: 8.75rem;
  height: 10rem;
  border-radius: 1.25rem;
  box-shadow: 0 0.625rem 1.5625rem rgba(13,202,240,0.4);
  transition: transform 0.3s ease;
  margin: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 1rem 0.5rem;
  gap: 0.5rem;
}

.box-icon:hover {
  transform: scale(1.2);
}

.box-icon i {
  font-size: 4rem;
  width: 4rem;
  height: 4rem;
  display: flex;
  align-items: center;
  justify-content: center;
}

.box-icon p {
  margin: 0;
  font-weight: 600;
  font-size: 1rem;
  text-align: center;
}

.icon-link a {
  text-decoration: none;
  color: #fff;
}
</style>