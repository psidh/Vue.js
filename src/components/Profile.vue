<!-- Profile.vue -->
<template>
  <div>
    <h1>{{ profile.Name }}</h1>
    <p>{{ profile.Profile }}</p>
    <img :src="profile.image" alt="Profile Image" style="max-width: 200px; border-radius: 10px;">
    <h2>Projects</h2>
    <ul>
      <li v-for="project in profile.projects" :key="project.id">
        <h3>{{ project.title }}</h3>
        <p>{{ project.description }}</p>
        <a :href="project.link" target="_blank">Visit Project</a>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      profile: {},
    };
  },
  mounted() {
    this.fetchProfileData();
  },
  methods: {
    fetchProfileData() {
      fetch("applications.json")
        .then((response) => response.json())
        .then((data) => {
          this.profile = data;
        })
        .catch((error) => {
          console.error("Error fetching profile data:", error);
        });
    },
  },
};
</script>

<style scoped>
</style>
