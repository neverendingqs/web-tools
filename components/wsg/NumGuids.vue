<template>
  <div class="input-group">
    <div class="input-group-prepend">
      <span id="num-guids-addon" class="input-group-text"
        >Number of Guids:</span
      >
    </div>
    <input
      v-model="numGuids"
      type="number"
      min="1"
      max="99"
      class="form-control"
      aria-label="NumGuids"
      aria-describedby="num-guids-addon1"
      @change="onChange"
    />
  </div>
</template>

<script>
export default {
  name: 'Guid',
  props: {},
  data() {
    return {
      numGuids: 10
    };
  },
  methods: {
    onChange() {
      this.$emit('change', this.numGuids);
    }
  }
};
</script>

<style scoped>
input {
  margin-right: 2px;
}
</style>
