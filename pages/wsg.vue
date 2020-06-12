<template>
  <div id="app">
    <h1>Waste Some GUIDs</h1>
    <div class="mb-1">
      <div class="form-inline justify-content-center">
        <NumGuids @change="generateMoreGuids" />
        <button v-clipboard:copy="allGuids" class="btn btn-primary">
          Copy All
        </button>
      </div>
    </div>
    <Guid v-for="guid in guids" :key="guid" :guid="guid" />
  </div>
</template>

<script>
import uuid from 'uuid/v4';
import Guid from '~/components/wsg/Guid.vue';
import NumGuids from '~/components/wsg/NumGuids.vue';
function generateGuids(numGuids = 10) {
  return [...Array(numGuids)].map(() => uuid());
}
export default {
  name: 'App',
  components: {
    Guid,
    NumGuids
  },
  data() {
    return {
      guids: generateGuids(),
      numGuids: 10
    };
  },
  computed: {
    allGuids() {
      return this.guids.join('\n');
    }
  },
  methods: {
    generateMoreGuids(numGuids) {
      const numGuidsBounded = Math.max(1, Math.min(999, numGuids));
      this.guids = generateGuids(numGuidsBounded);
    }
  }
};
</script>

<style scoped>
#app {
  text-align: center;
}
</style>
