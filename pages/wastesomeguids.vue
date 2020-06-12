<template>
  <div id="app" class="container">
    <h1>Waste Some GUIDs</h1>
    <hr />
    <div class="mb-1">
      <div class="form-inline justify-content-center">
        <NumGuids @change="generateMoreGuids" />
        <button v-clipboard:copy="allGuids" class="btn btn-info">
          Copy All
        </button>
      </div>
    </div>
    <Guid v-for="guid in guids" :key="guid" :guid="guid" />
  </div>
</template>

<script lang="ts">
import { v4 as uuid } from 'uuid';
import Guid from '~/components/wastesomeguids/Guid.vue';
import NumGuids from '~/components/wastesomeguids/NumGuids.vue';

function generateGuids(numGuids = 10): string[] {
  return [...Array(numGuids)].map(() => uuid());
}

export default {
  name: 'App',
  components: {
    Guid,
    NumGuids,
  },
  data() {
    return {
      guids: generateGuids(),
      numGuids: 10,
    };
  },
  computed: {
    allGuids(): string {
      return this.guids.join('\n');
    },
  },
  methods: {
    generateMoreGuids(numGuids: number) {
      const numGuidsBounded = Math.max(1, Math.min(999, numGuids));
      this.guids = generateGuids(numGuidsBounded);
    },
  },
};
</script>

<style>
#app {
  text-align: center;
}
</style>
