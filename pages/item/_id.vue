<template>
  <section class="section">
    <Item :item="item" />
  </section>
</template>

<script>
import Item from '~/components/Item.vue'
export default {
  // Components
  components: {
    Item
  },
  // SEO
  head() {
    return {
      titleTemplate: this.item.title,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'All there is to know about ' + this.item.title
        }
      ]
    }
  },
  async asyncData({ $axios, error, params }) {
    try {
      const { data } = await $axios.get(
        'http://localhost:4000/items/' + params.id
      )
      return {
        item: data
      }
    } catch (e) {
      error({
        statusCode: 503,
        message: 'Unable to fetch item #' + params.id
      })
    }
  }
}
</script>

<style scoped></style>
