<script>
import axios from 'axios';

export default {
  name: "ProjectList",
  data() {
    return {
      projects: [],
    };
  },
  async created() {
    try {
      const response = await axios.get('/api/projects');
      console.log('Fetched projects:', response.data); // Log the fetched data
      this.projects = response.data;
    } catch (error) {
      console.error('Error fetching projects:', error);
    }
  },
};
</script>

<template>
  <div class="project-list">
    <h2>Projects</h2>
    <p>Here are some of the projects I have worked on:</p>
    <div class="project-grid">
      <div class="project-card" v-for="project in projects" :key="project.id">
        <img :src="`/images/${project.image}`" :alt="project.title" class="project-image" />
        <h2 class="project-title">{{ project.title }}</h2>
        <p class="project-description">{{ project.description }}</p>
        <router-link :to="{ path: `/project/${project.id}` }" class="read-more-button">Read More</router-link>
      </div>
    </div>
  </div>
</template>

<style scoped>
.project-list {
  text-align: left; 
  padding: 1em;
}

.project-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 1em;
}

.project-card {
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 1em;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.project-image {
  width: 100%;
  height: auto;
  border-radius: 4px;
}

.project-title {
  font-size: 1.2em;
  margin: 0.5em 0;
}

.project-description {
  font-size: 1em;
  color: #666;
}

.read-more-button {
  display: inline-block;
  margin-top: 1em;
  padding: 0.5em 1em;
  background-color: #42b883;
  color: white;
  text-decoration: none;
  border-radius: 4px;
  text-align: center;
}

.read-more-button:hover {
  background-color: #333;
  color: #42b883;
}
</style>
