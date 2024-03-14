<script>
import axios from 'axios';
export default {
  data() {
    return {};
  },
  props: {
    post: Object,
    required: true,
  },
  methods: {},
};
</script>

<template>
  <div class="project-card">
    <div class="project-header">
      <h2>{{ post.title }}</h2>
    </div>
    <div class="project-body">
      <h4 class="content">{{ post.content }}</h4>
      <p>
        Category:<span>{{ post.category.title }}</span>
      </p>
      <p>
        Technology:<span
          v-for="technology in post.technologies"
          :key="technology.id"
          >{{ technology.title }},</span
        >
      </p>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.project-card {
  width: calc(30% - 20px); /* Sottrai lo spazio tra le card */
  margin-right: 20px; /* Spazio tra le card */
  margin-bottom: 20px; /* Spazio sotto le card */
  border-radius: 10px;
  overflow: hidden;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  background-color: #f5f5f5;
  transition: all 0.3s ease-in-out;

  &:hover {
    transform: translateY(-5px);
    box-shadow: 0 6px 15px rgba(0, 0, 0, 0.2);
  }

  .project-header {
    padding: 20px;
    background-color: #dc9ac9; /* Rosso */
    color: #ffffff;
    border-bottom: 1px solid #ccc;
    h2 {
      font-size: 1.8rem;
      color: #333;
      margin-bottom: 10px;
      text-align: center;
    }
  }
  .project-body {
    padding: 20px;
    color: #333;
    font-size: 1rem;

    h4 {
      font-size: 1rem;
      color: #333;
      margin-bottom: 10px;
    }

    p {
      font-size: 1.2rem;
      color: #0b0a0a;
      margin-bottom: 20px;
    }
    span {
      font-size: 1.2rem;
      color: #666;
      margin-bottom: 20px;
    }
  }
}
</style>
