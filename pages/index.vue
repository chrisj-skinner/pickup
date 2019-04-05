<template>
  <div>
    <Logo />
    <h1 class="title">..pickup..</h1>
    <h2 class="subtitle">Pickup app built on nuxtjs</h2>
    <div class="content">
      <Navbar />
    </div>
    <div class="columns">
      <ItemCard
        v-for="(item, index) in items"
        :key="index"
        :item="item"
        :data-index="index"
        class="column is-half"
      ></ItemCard>
    </div>
  </div>
</template>

<script>
import Logo from '~/components/Logo.vue'
import Navbar from '~/components/Navbar.vue'
import ItemCard from '~/components/ItemCard.vue'

export default {
  // Components
  components: {
    Logo,
    Navbar,
    ItemCard
  },
  // SEO
  head() {
    return {
      title: 'Welcome'
    }
  },
  // Call the local server and catch any errors
  async asyncData({ $axios, error }) {
    try {
      const { data } = await $axios.get('http://localhost:4000/items')
      return {
        items: data
      }
    } catch (e) {
      error({
        statusCode: 503,
        message: 'Unable to fetch items at this time Please try again.'
      })
    }
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}
</style>
