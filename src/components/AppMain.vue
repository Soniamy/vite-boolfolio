<script>
import axios from 'axios';
import ProjectCard from './ProjectCard.vue';
export default {
  data() {
    return {
      posts: [],
      currentPage: 1,
      totalPages: 1,
    };
  },
  components: {
    ProjectCard,
  },
  mounted() {
    this.fetchProjects();
  },
  methods: {
    async fetchProjects(page = 1) {
      try {
        const response = await axios.get(
          `http://127.0.0.1:8000/api/posts?page=${page}`
        );
        this.posts = response.data.results.data;
        this.currentPage = response.data.results.current_page;
        this.totalPages = response.data.results.last_page;
      } catch (error) {
        console.error('Errore durante la richiesta API:', error);
      }
    },
    async nextPage() {
      await this.fetchProjects(this.currentPage + 1);
    },
    async prevPage() {
      await this.fetchProjects(this.currentPage - 1);
    },
  },
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
    <div class="pagination">
      <button
        @click="prevPage"
        :disabled="currentPage === 1"
        class="pagination-btn"
      >
        Pagina precedente
      </button>
      <span class="pagination-info"
        >Pagina {{ currentPage }} di {{ totalPages }}</span
      >
      <button
        @click="nextPage"
        :disabled="currentPage === totalPages"
        class="pagination-btn"
      >
        Pagina successiva
      </button>
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
.pagination {
  margin-top: 16px;
  display: flex;
  justify-content: center;

  .pagination-btn {
    padding: 8px 16px;
    font-size: 1rem;
    background-color: #d04bda;
    color: #fff;
    border: none;
    border-radius: 4px;
    cursor: pointer;

    &:hover {
      background-color: #a700b3;
    }

    &:disabled {
      background-color: #ccc;
      cursor: not-allowed;
    }
  }

  .pagination-info {
    font-size: 1rem;
    color: #555;
    margin: 8px 10px;
  }
}
</style>
