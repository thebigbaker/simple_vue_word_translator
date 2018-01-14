<template>
  <div id="app" class="container text-center">
    <h1>Word Translator</h1>
    <h5>Powered By Vue.js 2</h5>
    <hr>
    <TranslateForm @formSubmit="translateText"></TranslateForm>
    <br>
    <TranslateOutput v-text="translatedText"></TranslateOutput>   
  </div>
</template>

<script>
  import TranslateForm from './components/TranslateForm.vue'
  import TranslateOutput from './components/TranslateOutput.vue'

  export default {
    components: {
      TranslateForm,
      TranslateOutput
    },

    data() {
      return {
        translatedText: ''
      }
    },

    methods: {
      translateText: function(text, language) {
        this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20180114T160018Z.2b9b71fe65da9dce.e3bb535bdc4289afcc3fd9ebc501bc86931086f4&lang='+language+'&text='+text)
        .then((response) => {
          this.translatedText = response.body.text[0];
        })
      }
    }
  }
</script>

<style>
  body {
    background: #fefefe;
  }
</style>
