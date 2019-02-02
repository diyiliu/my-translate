<template>
  <div id="app">
    <h1>在线翻译</h1>
    <h5 class="text-muted">简单 / 易用 / 快捷</h5>
    <TranslateForm v-on:tlForm="translateText"/>
    <TranslateOutput v-bind:translatedText="result"/>
  </div>
</template>

<script>
  import TranslateForm from './components/TranslateForm'
  import TranslateOutput from './components/TranslateOutput'

  const apiKey = 'trnsl.1.1.20190201T012200Z.e9f3083d06bae8cc.1c0e3ab3171489a8e868fb2bceb3c237ba713d60';
  export default {
    name: 'App',
    components: {
      TranslateForm,
      TranslateOutput
    },
    data: function () {
      return {
        result: ''
      }
    },
    methods: {
      translateText: function (text, lang) {
        this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate' +
          '?key=' + apiKey +
          '&text=' + text +
          '&lang=' + lang).then((response) => {
          this.result = response.body.text[0];
        })
      }
    }
  }
</script>

<style>
  @import "assets/bootstap-materia.css";

  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>
