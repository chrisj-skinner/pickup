<template>
  <div>
    <h1>Item #{{ this.$route.params.id }}</h1>
  </div>
</template>

<script>
export default {
  head() {
    return {
      titleTemplate: 'Item #' + this.id,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'All there is to know about Item #' + this.id
        }
      ]
    }
  },
  computed: {
    id() {
      return this.$route.params.id
    }
  }
}
</script>

<style scoped></style>
