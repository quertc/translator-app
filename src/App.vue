<template>
  <div id="app">
    <h1>Translator App</h1>
    <h4>Powered by Vue.js and Yandex API</h4>
    <TranslateForm @formSubmit="translateText" @showError="errorHandling"></TranslateForm>
    <TranslateOutput :output="translatedText" :class="{error: isError}"></TranslateOutput>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm.vue';
import TranslateOutput from './components/TranslateOutput.vue';

export default {
  name: 'app',
  components: {
    TranslateForm,
    TranslateOutput
  },
  data() {
    return {
      translatedText: '',
      isError: false
    };
  },
  methods: {
    translateText(text, language) {
      this.$http.get(`https://translate.yandex.net/api/v1.5/tr.json/translate?key=${process.env.VUE_APP_SECRET}&lang=${language}&text=${text}`)
      .then(response => {
        this.translatedText = response.body.text[0];  
      })
      .catch(() => {
        this.isError = true;
        this.translatedText = 'An error occurred while translating the text. Details in the browser console.';
      });
    },
    errorHandling(errorText) {
      this.isError = true;
      this.translatedText = errorText;
    }
  }
};
</script>

<style>
* {
  font-family: Montserrat, Arial, sans-serif;
}

#app {
  display: grid;
  justify-items: center;
}

h1 {
  margin-bottom: 0;
  font-size: 1.4em;
  color: rgb(51, 51, 51);
}

h4 {
  margin-top: 10px;
  margin-bottom: 26px;
  font-size: 0.9em;
  color: rgb(51, 51, 51);
  font-weight: 400;
}

#app .error {
  color: rgb(240, 0, 0);
}
</style>
