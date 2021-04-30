<template>
  <div class="error-block">
    <h1>{{this.error.message}}</h1>
    <h2>{{this.error.statusCode}}</h2>
  </div>
</template>

<script>
  export default {
    props: {
      error: {
        type: Object,
        default: () => ({})
      }
    },
    mounted() {
      console.log(this.error, 'ERROR_OBJECT')
    }
  }
</script>

<style lang="scss" scoped>
  .error-block {
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    height: 100vh;
  }
</style>
