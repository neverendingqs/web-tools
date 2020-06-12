<template>
  <div>
    <Nav />
    <div class="container">
      <nuxt />
    </div>
  </div>
</template>

<script>
import Nav from '~/components/Nav.vue';

export default {
  components: {
    Nav
  }
};
</script>

<style>
.container {
  padding-top: 50px;
}
</style>
