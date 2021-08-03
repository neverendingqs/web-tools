<template>
  <div class="form-inline justify-content-center">
    <!-- eslint-disable-next-line vue/no-mutating-props -->
    <input v-model="guid" type="text" readonly="" class="form-control" />
    <button v-clipboard:copy="guid" class="btn btn-primary">Copy</button>
  </div>
</template>

<script>
export default {
  name: 'Guid',
  props: {
    guid: {
      type: String,
      default: '(none)',
    },
  },
};
</script>

<style scoped>
input {
  margin: 2px;
  text-align: center;
  width: 325px !important; /* TODO: fix */
}
</style>
