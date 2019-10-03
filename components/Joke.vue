<template>
  <nuxt-link :to="'/jokes/' + id">
    <p class="p-2 border-dotted border-4 border-gray-200">{{ joke }}</p>
  </nuxt-link>
</template>

<script>
export default {
  name: 'Joke',

  props: ['joke', 'id']
}
</script>
