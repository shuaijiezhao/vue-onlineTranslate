<template>
  <div id="translateOutput">
   <input type="text" v-model="translatedText">
  </div>
</template>

<script>
export default {
  name: 'translateOutput',
  props: ['translatedText']
}
</script>

<style>

</style>
