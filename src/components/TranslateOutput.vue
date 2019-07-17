<template>
  <span class="translatedText">{{ outputText }}</span>
</template>

<script>
export default {
  name: 'TranslateOutput',
  props: {
    outputText: {
      type: String,
      required: true
    }
  }
};
</script>

<style scoped>
.translatedText {
  text-align: center;
  max-width: 768px;
  padding: 0 2px 0 2px;
  margin-top: 45px;
  word-wrap: break-word;
  color: rgb(51, 51, 51);
}
</style>
