<script>
import axios from 'axios';
import ProjectCard from './ProjectCard.vue';
export default {
  data() {
    return {
      posts: [],
    };
  },
  components: {
    ProjectCard,
  },
  created() {
    axios.get('http://127.0.0.1:8000/api/posts').then((res) => {
      console.log(res.data);
      this.posts = res.data.results.data;
    });
  },
  methods: {},
};
</script>

<template>
  <main>
    <div id="app">
      <h1 class="app-title">Projects</h1>
      <div class="cards-container">
        <ProjectCard v-for="post in posts" :key="post.id" :post="post" />
      </div>
    </div>
  </main>
</template>

<style lang="scss" scoped>
main {
  background-color: rgb(240, 221, 232);
}
.app-title {
  font-size: 2rem;
  margin-bottom: 16px;
  color: rgb(152, 114, 150);
}

.cards-container {
  width: 100%;
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
}
</style>
