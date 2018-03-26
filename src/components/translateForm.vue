<template>
  <div id="translateForm" class="row">
    <div class="col-md-6 col-md-offset-3">
      <form id="transForm" class="well form-inline" @submit="formSubmit">
        <input class="form-control" type="text" v-model="toTranslate" placeholder="请输入需要翻译的内容">
        <select class="form-control" v-model="language">
          <option value="en">English</option>
          <option value="ru">Russian</option>
          <option value="ko">Korean</option>
          <option value="ja">Janpenese</option>
        </select>
        <input class="btn btn-primary" type="submit">
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'translateForm',
  data() {
    return {
      toTranslate: '',
      language: ''
    }
  },
  methods: {
    formSubmit(e) {
      // alert(this.toTranslate)
      if (this.toTranslate) {
        this.$emit('submitForm', this.toTranslate, this.language)
        e.preventDefault()
      }   
    }
  },
  created() {
    this.language = 'en'
  }
}
</script>

<style>
#transForm {
  border-radius: 5px;
  border: 1px #ccc solid;
}
</style>
