<template>
  <span class="translatedText">{{ translatedText }}</span>
</template>

<script>
export default {
  name: 'translateOutput',
  props: ['translatedText']
};
</script>

<style scoped>

.translatedText {
  max-width: 450px;
  padding: 12px;
  margin-top: 45px;
  word-wrap: break-word;
  color: rgb(51,51,51);
}

</style>
