<template>
  <div class="container">
    <form
      class="form container__form"
      @submit.prevent="$emit('form-submit', textToTranslate, selectedLanguage)"
    >
      <textarea
        v-model.trim="textToTranslate"
        placeholder="Enter text"
        class="form__textarea"
      />
      <select
        v-model="selectedLanguage"
        class="form__select"
      >
        <option
          value=""
          disabled
        >
          Select a language
        </option>
        <option
          v-for="(language, code, index) of availableLanguages"
          :key="index"
          :value="code"
        >
          {{ language }}
        </option>
      </select>
      <input
        :disabled="isDisabled"
        type="submit"
        value="Translate"
        class="form__submit"
        :class="{ form__submit_disabled: isDisabled }"
      >
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      textToTranslate: '',
      availableLanguages: {},
      selectedLanguage: '',
    };
  },
  computed: {
    isDisabled() {
      return !(this.textToTranslate && this.selectedLanguage);
    },
  },
  mounted() {
    this.$http.get(`https://translate.yandex.net/api/v1.5/tr.json/getLangs?key=${process.env.VUE_APP_SECRET}&ui=en`)
      .then(response => {
        this.availableLanguages = response.body.langs;
      })
      .catch(() => {
        this.$emit('show-error', 'An error occurred while searching for available languages.');
      });
  },
};
</script>

<style scoped>
.form {
  display: flex;
  flex-flow: column;
  padding: 25px;
  transition: box-shadow .55s;
  border-radius: 8px;
  box-shadow: 0 10px 26px rgba(0, 0, 0, .07);
}

.container__form {
  margin-bottom: 45px;
}

.form:hover {
  box-shadow: 0 10px 20px rgba(0, 0, 0, .1);
}

.form__textarea {
  height: 30px;
  margin-bottom: 12px;
  padding: 3px 6px;
  resize: vertical;
  border: 0;
  border-bottom: 1px solid #3f3f3f;
  border-radius: 0;
  font-size: 14px;
  line-height: 30px;
}

.form__textarea::placeholder {
  opacity: .9;
  color: #363636;
}

.form__select {
  margin-bottom: 12px;
  padding: 5px;
  cursor: pointer;
  text-align: center;
  border: 0;
}

.form__submit {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 8px;
  cursor: pointer;
  transition: background-color .48s, color .48s;
  border: 1px solid #3f3f3f;
  border-radius: 8px;
  background: none;
}

.form__submit_disabled {
  opacity: .88;
}

.form__submit:hover {
  color: #fff;
  background-color: #3f3f3f;
}
</style>
