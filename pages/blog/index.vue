<template>
  <div class="container">
    <Navigation />
    <Blog />
  </div>
</template>

<script>
import Navigation from '~/components/Navigation.vue'
export default {
  components: { Navigation },

}
</script>

<style lang="scss" scoped>
.container {
  margin: 0;
  padding: 0;
  min-height: 100vh;
  display: flex;
  justify-content: center;

  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
}

</style>
