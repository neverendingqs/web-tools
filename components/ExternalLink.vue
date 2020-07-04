<template>
  <a :class="classes" :href="href" target="_blank" rel="noopener noreferrer">
    <slot></slot><sup>🔗</sup>
  </a>
</template>

<script>
export default {
  name: 'ExternalLink',
  props: {
    classes: {
      type: String,
      default: '',
    },
    href: {
      type: String,
      default: '',
    },
  },
};
</script>
