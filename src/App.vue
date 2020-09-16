<template>
  <div id="app">
    <div class="translator">
      <h1 class="translator__title">
        Translator App
      </h1>
      <h4 class="translator__description">
        Powered by Vue.js and Yandex API
      </h4>
      <TranslateForm
        @form-submit="translateText"
        @show-error="errorHandling"
      />
      <TranslateOutput
        :output-text="translatedText"
        :class="{ 'translated-text_error': isError }"
      />
    </div>
  </div>
</template>

<script>
import TranslateForm from '@/components/TranslateForm.vue';
import TranslateOutput from '@/components/TranslateOutput.vue';

export default {
  name: 'App',
  components: {
    TranslateForm,
    TranslateOutput,
  },
  data() {
    return {
      translatedText: '',
      isError: false,
    };
  },
  methods: {
    translateText(text, language) {
      this.$http.get(`https://translate.yandex.net/api/v1.5/tr.json/translate?key=${process.env.VUE_APP_SECRET}&lang=${language}&text=${text}`)
        .then(response => {
          [this.translatedText] = response.body.text;
        })
        .catch(() => {
          this.translatedText = 'An error occurred while translating the text.';
          this.isError = true;
        });
    },
    errorHandling(errorText) {
      this.translatedText = errorText;
      this.isError = true;
    },
  },
};
</script>

<style>
* {
  color: #333;
  font-family: Montserrat, Arial, sans-serif;
}

#app {
  display: flex;
  justify-content: center;
}

.translator {
  display: flex;
  flex-flow: column;
  align-items: center;
}

.translator__title {
  margin-bottom: 0;
  font-size: 22px;
}

.translator__description {
  margin: 10px 0 26px 0;
  font-size: 15px;
  font-weight: 400;
}
</style>
