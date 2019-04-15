<template>
  <span class="translatedText">{{ output }}</span>
</template>

<script>
export default {
  name: 'translateOutput',
  props: ['output']
};
</script>

<style scoped>
.translatedText {
  max-width: 768px;
  padding: 0 2px 0 2px;
  margin-top: 45px;
  word-wrap: break-word;
  color: rgb(51, 51, 51);
}
</style>
