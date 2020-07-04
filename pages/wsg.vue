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

      <div class="form-group">
        <div class="custom-control custom-switch">
          <input
            id="capitalizeSwitch"
            v-model="capitalize"
            type="checkbox"
            class="custom-control-input"
            @change="changeCasing"
          />
          <label class="custom-control-label" for="capitalizeSwitch">
            Capitalize
          </label>
        </div>
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
    NumGuids,
  },
  data() {
    return {
      capitalize: false,
      guids: generateGuids(),
      numGuids: 10,
    };
  },
  computed: {
    allGuids() {
      return this.guids.join('\n');
    },
  },
  methods: {
    changeCasing() {
      this.guids = this.capitalize
        ? this.guids.map((guid) => guid.toUpperCase())
        : this.guids.map((guid) => guid.toLowerCase());
    },

    generateMoreGuids(numGuids) {
      const numGuidsBounded = Math.max(1, Math.min(999, numGuids));
      this.guids = generateGuids(numGuidsBounded);
      this.changeCasing();
    },
  },
};
</script>

<style scoped>
#app {
  text-align: center;
}
</style>
