<template>
  <div id="app">
    <h1>在线翻译</h1>
    <h5 class="text-muted">简单 / 易用</h5>
    <translateForm @submitForm="fromSubmit"></translateForm>
    <div>
      <translateOutput v-text.trim="translatedText"></translateOutput>  
    </div>
  </div>
</template>

<script>
import translateForm from './components/translateForm'
import translateOutput from './components/translateOutput'

export default {
  name: 'App',
  data() {
    return {
      translatedText: ''
    }
  },
  methods: {
    fromSubmit(text, language) {
      // alert(text)
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20180314T003702Z.82ea0da9cef18ada.28a80248163772b253adddf0ab742c1ca491ba90&lang='+language+'&text='+text)
          .then((response) => {
            // console.log(response.body.text[0]);
            this.translatedText = response.body.text[0]
          })
    }
  },
  components: {
    translateForm, translateOutput
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
