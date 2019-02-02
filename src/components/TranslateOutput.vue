<template>
  <div id="translateOutput">
        <h3 class="m-2 text-info">{{translatedText}}</h3>
  </div>
</template>

<script>
  export default {
    name: "translateOutput",
    props: [
      'translatedText'
    ]
  }
</script>

<style scoped>

</style>
