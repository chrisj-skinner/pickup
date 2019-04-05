<template>
  <section class="section">
    <form @submit.prevent="createItem">
      <!-- BaseInput -->
      <BaseInput
        v-model="item.title"
        type="text"
        label="Title"
        placeholder="Title"
      />

      <div class="field">
        <label class="label">Category</label>
        <div class="control">
          <div class="select">
            <select>
              <option>Select dropdown</option>
              <option>Applicance</option>
              <option>Clothes</option>
              <option>Funiture</option>
              <option>Toys</option>
            </select>
          </div>
        </div>
      </div>

      <div class="field">
        <label class="label">Description</label>
        <div class="control">
          <textarea class="textarea" placeholder="Textarea"></textarea>
        </div>
      </div>

      <!-- BaseInput -->
      <!-- <BaseInput label="Location" placeholder="Enter a location" /> -->

      <div class="field">
        <div class="control">
          <label class="checkbox">
            <input type="checkbox" />
            I agree to the
            <a href="#">terms and conditions</a>
          </label>
        </div>
      </div>

      <div class="field is-grouped">
        <div class="control">
          <button class="button is-link">Submit</button>
        </div>
        <div class="control">
          <button class="button is-text">Cancel</button>
        </div>
      </div>
    </form>
  </section>
</template>

<script>
import BaseInput from '~/components/BaseInput.vue'

export default {
  components: {
    BaseInput
  },
  // SEO
  head() {
    return {
      title: 'Create',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'Create an item'
        }
      ]
    }
  },
  data() {
    return {
      item: this.createFreshEventObject()
    }
  },

  methods: {
    async createItem({ $axios }) {
      // console.log(this.item)
      // try {
      await $axios.post('http://localhost:4000/items' + this.item)
      // } catch (e) {
      //   error({
      //     statusCode: 503,
      //     message: 'Unable to send request at this time.'
      //   })
      // }
    },
    createFreshEventObject() {
      const id = Math.floor(Math.random() * 10000000)

      return {
        id: id,
        category: '',
        title: '',
        description: '',
        location: '',
        date: '',
        time: ''
      }
    }
  }
}
</script>

<style scoped></style>
