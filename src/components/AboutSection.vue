<template>
  <section id="about">
    <div class="about-wrapper">
      <img class="about-image" src="/undraw_programming_65t2.svg" alt="avatar" />
      <div class="about-content">
        <h1 class="headings">About me</h1>
        <p class="about-text">
          Hello, my name is Ray.
          I've been passionate about computers and software from a young age — ever since I was 11 years old,
          I've been fascinated by how technology works and how it can be used to build, solve, and create.
          I started coding in my teenage years and quickly fell in love with the process of turning ideas into real, working applications.
          Since then, I've been dedicated to continuously learning and improving my skills,
          exploring everything from front-end design to back-end development. Whether it's mastering a new framework, working on a team project,
          or building something from scratch, I'm always eager to expand my knowledge and grow as a developer.
          For me, software development isn't just a career path — it's a lifelong passion.
        </p>
        <br />
        <button type="button" class="btn btn-info">Download CV</button>
      </div>
    </div>
  </section>
</template>

<script setup>
// no data or logic needed here — purely static content
</script>

<style scoped>
#about {
  font-family: "Poppins", sans-serif;
  max-width: 75rem;
  margin: 0 auto;
  padding: 5rem 1.25rem;
  color: #ffffff;
}

.btn-info {
  transition: background-color 0.8s, transform 0.3s ease, color 0.8s;
  border: gray;
}

.btn-info:hover {
  background: gray;
  color: #fff;
  transform: scale(1.1) translateY(-0.3125rem);
}

.about-wrapper {
  display: flex;
  align-items: flex-start;
  gap: 2.5rem;
}

.about-image {
  width: 21.875rem;
  height: 25rem;
  border-radius: 1.25rem;
}

.about-content {
  flex: 1;
  margin: 0;
  padding: 0;
}

.about-content h1 {
  margin: 0 0 0.9375rem 0;
  position: relative;
}

.about-content h1::after {
  content: "";
  position: absolute;
  left: 0;
  bottom: -0.625rem;
  width: 3.125rem;
  height: 0.1875rem;
  background: #34d4ec;
}

.about-text {
  font-size: 1rem;
  line-height: 1.7;
  margin: 1.25rem 0 0 0;
  padding: 0;
}

@media (max-width: 48rem) {
  .about-wrapper {
    flex-direction: column;
    gap: 1.875rem;
  }
  .about-image {
    width: 100%;
    max-width: 21.875rem;
  }
}
</style>