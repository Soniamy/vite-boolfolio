<script>
import axios from 'axios';
export default {
  data() {
    return {
      posts: [],
    };
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
    <h1>Tutti i Post!</h1>
    <div>
      <div v-for="post in posts" :key="post.id">
        {{ post.title }}
      </div>
    </div>
  </main>
</template>

<style lang="scss" scoped></style>
