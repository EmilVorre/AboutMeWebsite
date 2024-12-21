<script setup lang="ts">
import Navbar from './components/Navbar.vue'
import './assets/global.css'
import AboutMe from './components/AboutMe.vue'
import Footer from './components/Footer.vue'
import ProjectList from './components/ProjectList.vue'
</script>

<template>
  <Navbar />
  <div class="content">
    <div class="about-me-container">
      <AboutMe />
    </div>
    <ProjectList />
  </div>
  <Footer />
</template>

<style scoped>
body, html {
  margin: 0;
  padding: 0;
  width: 100%;
  height: 100%;
}

.content {
  padding-top: 4em;
  padding-bottom: 4em;
}

.about-me-container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  text-align: center;
  padding: 2em;
}
</style>
