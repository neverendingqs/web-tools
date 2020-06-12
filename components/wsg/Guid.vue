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
      default: '(none)'
    }
  }
};
</script>

<style scoped>
input {
  margin: 2px;
  width: 350px;
}
</style>
