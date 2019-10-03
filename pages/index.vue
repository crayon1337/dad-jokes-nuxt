<template>
  <div>
    <Joke v-for="joke in jokes" :key="joke.id" :joke="joke.joke" :id="joke.id"/>
  </div>
</template>

<script>
import axios from 'axios'
import Joke from '../components/Joke'

export default {
  data() {
    return {
      jokes: []
    }
  },

  head() {
    return {
      title: 'Dad jokes',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: "Best place for corny jokes"
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
      const response = await axios.get('https://icanhazdadjoke.com/search', config)
      this.jokes = response.data.results;
    } catch(err) { console.log(err); }
  }

};
</script>
