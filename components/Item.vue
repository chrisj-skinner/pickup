<template>
  <article>
    <figure class="image is-square">
      <img src="https://bulma.io/images/placeholders/128x128.png" />
    </figure>
    <h4 class="has-text-left">{{ item.title }}</h4>
    <p class="has-text-left is-size-7">{{ parsedDate }} @{{ item.time }}</p>
  </article>
</template>

<script>
export default {
  props: {
    // eslint-disable-next-line
    item: Object
  },
  computed: {
    parsedDate() {
      const itemDate = new Date(this.item.date)
      return itemDate.toDateString()
    }
  }
}
</script>

<style scoped></style>
