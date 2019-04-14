<template>
  <nuxt-link :to="'/item/' + item.id">
    <article class="box">
      <figure class="image is-square">
        <img src="https://bulma.io/images/placeholders/128x128.png" />
      </figure>
      <h4 class="has-text-left">{{ item.title }}</h4>
      <p class="has-text-left is-size-7">{{ parsedDate }} @{{ item.time }}</p>
    </article>
  </nuxt-link>
</template>
<script>
export default {
  name: 'ItemCard',
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
