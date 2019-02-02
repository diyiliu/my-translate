<template>
  <div class="container" id="translateForm">
    <div class="row justify-content-center">
      <form id="tlForm" class="form-inline p-5" v-on:submit="formSubmit">
        <input class="form-control" type="text" v-model="textToTranslate" placeholder="输入需要翻译的内容">
        <select class="form-control mx-2"  v-model="language">
          <option value="en">English</option>
          <option value="ru">Russian</option>
          <option value="ja">Japanese</option>
          <option value="ko">Korean</option>
          <option value="fr">French</option>
        </select>
        <input class="btn btn-primary" type="submit" value="翻译">
      </form>
    </div>
  </div>
</template>

<script>
  export default {
    name: "translateForm",
    data: function () {
      return {
        textToTranslate: '',
        language: ''
      }
    },
    methods: {
      formSubmit: function (e) {
        this.$emit('tlForm', this.textToTranslate, this.language);
        e.preventDefault();
      }
    },
    created() {
      this.language = 'en'
    }
  }
</script>

<style scoped>
#tlForm{
  border-radius: 10px;
  border: 1px solid #c1c1c1;
}
</style>
