<template>
  <div>
    <h1>{{ name }}</h1>
    <p>{{ loaded }}</p>
  </div>
</template>

<script>
export default {
  loading: false,
  asyncData() {
    return new Promise((resolve) => {
      setTimeout(() => resolve({
        loaded: false,
        name: 'Nuxt.js'
      }), 10)
    })
  },
  mounted() {
    setTimeout(() => {
      this.$nuxt.$loading.finish()
      setTimeout(() => {
        // Re-enable loader as we move on
        // to normal pages in the test
        this.$nuxt.$loading.start()
        this.loaded = true
      }, 1500)
    }, 1500)
  }
}
</script>
