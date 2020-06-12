<template>
  <div class="form-inline justify-content-center">
    <input v-model="guid" type="text" readonly="" class="form-control" />
    <button v-clipboard:copy="guid" class="btn btn-info">Copy</button>
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

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
input {
  margin: 2px;
  width: 350px !important; /* TODO: fix */
}
</style>
