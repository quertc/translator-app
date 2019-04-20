<template>
  <div id="translateForm">   
    <form class="form" @submit.prevent="formSubmit">
      <textarea class="form__textarea" v-model="textToTranslate" placeholder="Введите текст ..." required></textarea>
      <select class="form__select" v-model="language" required>
        <option v-for="(language, code, index) of availablelanguages" v-bind:value="code" :key="index">{{ language }}</option>
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
    this.language = 'ru';
    this.$http.get(`https://translate.yandex.net/api/v1.5/tr.json/getLangs?key=${process.env.VUE_APP_SECRET}&ui=ru`)
    .then(response => {
      this.availablelanguages = response.body.langs;
    })
    .catch(() => {
      this.$emit('showError', 'An error occurred while searching for available languages. Details in the browser console');
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
  box-shadow: 0 .5rem 4rem rgba(0, 0, 0, .06);
  padding: 25px;
  border-radius: 7px;
  transition: box-shadow .45s;
  cursor: pointer;
}

.form:hover {
  box-shadow: 0 .5rem  1rem rgba(0, 0, 0, .14);
}

.form__textarea {
  font-family: 'Montserrat';
  height: 30px;
  line-height: 30px;
  resize: vertical;
  padding: 3px;
  outline: none;
  font-size: .9em;
  border: none;
  border-bottom: 1px solid rgb(63, 63, 63);
  color: rgb(51, 51, 51);
}

.form__textarea::placeholder {
  color: rgb(77, 77, 77);
}

.form__select {
  font-family: 'Montserrat';
  text-align: center;
  border: none;
  cursor: pointer;
  padding: 5px;
  outline: none;
  color: rgb(51, 51, 51);
}

.form__submit {
  font-family: 'Montserrat';
  cursor: pointer;
  display: flex;
  justify-content: center;
  align-items: center;
  background: none;
  outline: none;
  padding: 7.5px;
  border: 1px solid rgb(63, 63, 63);
  border-radius: 7.5px;
  transition: background-color .45s, color .45s;
  color: rgb(51, 51, 51);
}

.form__submit:hover {
  background-color: rgb(63, 63, 63);
  color: rgb(255, 255, 255);
}
</style>
