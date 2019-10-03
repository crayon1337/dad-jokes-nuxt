<template>
  <div>
    <h3>Joke: {{ joke.joke }}</h3>
    <hr>
    <h6>ID: {{ $route.params.id }}</h6>
    <nuxt-link to="/" class="bg-red-500 hover:bg-red-700 text-white font-bold rounded">Back to Jokes</nuxt-link>
  </div>
</template>

<script>
import axios from 'axios'
import Joke from '../../../components/Joke'

export default {
  data() {
    return {
      joke: []
    }
  },

  head() {
    return {
      title: this.joke.joke + ' | Dad Jokes',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: "icanhazdadjoke.com is the largest selection of dad jokes on the internet. Now supporting many different integrations to ensure you can access the dad jokes that you need wherever you are."
        }
      ]
    }
  },

  components: {
    Joke
  },

  async created() {
    const config = {
      headers: {
        Accept: 'application/json'
      }
    }

    try {
      const response = await axios.get(`https://icanhazdadjoke.com/j/${this.$route.params.id}`, config);
      this.joke = response.data;
    } catch(err) { console.log(err) }
  }
}
</script>
