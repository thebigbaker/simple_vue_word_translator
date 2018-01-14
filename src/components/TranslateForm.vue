<template>
  <div id="translateForm" class="row">
    <div class="col-md-6 offset-md-4">
      <form @submit="formSubmit" class="form-inline well">
        <div class="form-group">
          <input class="form-control mr-3" type="text" v-model="textToTranslate" placeholder="Enter a word...">
          <select v-model="language" class="form-control mr-3">
            <option value="ru">Russian</option>
            <option value="es">Spanish</option>
            <option value="fr">French</option>
            <option value="it">Italian</option>
          </select>
          <input class="btn btn-primary"type="submit" value="Translate">
        </div>   
      </form>
    </div>    
  </div>
</template>

<script>
  export default {

    data() {
      return {
        textToTranslate: '',
        language: ''
      }
    },

    created(){
      this.language = 'ru';
    },

    methods: {
      formSubmit(e) {
        this.$emit('formSubmit', this.textToTranslate, this.language);
        e.preventDefault();
      }
    }

  }
</script>

<style>
 
</style>