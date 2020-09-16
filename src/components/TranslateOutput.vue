<template>
  <span class="translated-text">{{ outputText }}</span>
</template>

<script>
export default {
  props: {
    outputText: {
      type: String,
      required: true,
    },
  },
};
</script>

<style scoped>
.translated-text {
  max-width: 768px;
  padding: 0 2px 0 2px;
  text-align: center;
  word-wrap: break-word;
}

.translated-text_error {
  color: #f00000;
}
</style>
