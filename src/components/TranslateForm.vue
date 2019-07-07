<template>
  <div id="translateForm">   
    <form class="form" @submit.prevent="formSubmit">
      <textarea class="form__textarea" v-model="textToTranslate" placeholder="Enter text" required></textarea>
      <select class="form__select" v-model="language" required>
        <option value="select" disabled>Select a language</option>
        <option v-for="(language, code, index) of availablelanguages" :value="code" :key="index">{{ language }}</option>
      </select>
      <input class="form__submit" type="submit" value="Translate">
    </form>   
  </div>
</template>

<script>
export default {
  name: 'translateForm',
  data() {
    return {
      textToTranslate: '',
      availablelanguages: {},
      language: ''
    };
  },
  created() {
    this.language = 'select';
    this.$http.get(`https://translate.yandex.net/api/v1.5/tr.json/getLangs?key=${process.env.VUE_APP_SECRET}&ui=en`)
    .then(response => {
      this.availablelanguages = response.body.langs;
    })
    .catch(() => {
      this.$emit('showError', 'An error occurred while searching for available languages. Details in the browser console.');
    })
  },
  methods: {
    formSubmit() {
      this.$emit('formSubmit', this.textToTranslate, this.language);
    }
  }
};
</script>

<style scoped>
.form {
  display: grid;
  grid-gap: 12px;
  background-color: rgb(255, 255, 255);
  box-shadow: 0 0.5rem 4rem rgba(0, 0, 0, 0.068);
  padding: 25px;
  border-radius: 7px;
  transition: box-shadow 0.55s;
  cursor: pointer;
}

.form:hover {
  box-shadow: 0 0.5rem 2.5rem rgba(0, 0, 0, 0.088);
}

.form__textarea {
  height: 30px;
  line-height: 30px;
  resize: vertical;
  padding: 3px;
  outline: none;
  font-size: 0.9em;
  border: none;
  border-bottom: 1px solid rgb(63, 63, 63);
  color: rgb(51, 51, 51);
}

.form__textarea::placeholder {
  color: rgb(54, 54, 54);
  opacity: 0.9;
}

.form__select {
  text-align: center;
  border: none;
  cursor: pointer;
  padding: 5px;
  outline: none;
  color: rgb(51, 51, 51);
}

.form__submit {
  cursor: pointer;
  display: flex;
  justify-content: center;
  align-items: center;
  background: none;
  outline: none;
  padding: 7.5px;
  border: 1px solid rgb(63, 63, 63);
  border-radius: 7.5px;
  transition: background-color 0.48s, color 0.48s;
  color: rgb(51, 51, 51);
}

.form__submit:hover {
  background-color: rgb(63, 63, 63);
  color: rgb(255, 255, 255);
}
</style>
