<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import AppFooter from './components/AppFooter.vue';

export default {
  data() {
    return {};
  },
  components: {
    AppHeader,
    AppMain,
    AppFooter,
  },
  methods: {},
};
</script>

<template>
  <h1 class="title">BoolFolio Projects</h1>

  <AppHeader />

  <AppMain />

  <AppFooter />
</template>

<style lang="scss">
@use 'assets/scss/main' as *;
@import 'assets/scss/partials/reset';
.title {
  font-size: 4rem;
  margin-bottom: 16px;
  color: rgb(76, 45, 72);
}
</style>
