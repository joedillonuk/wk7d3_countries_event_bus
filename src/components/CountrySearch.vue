<template lang="html">
  <div>
    <input v-model="message" placeholder="Search">
    <button v-on:click="handleClick">Search</button>
  </div>
</template>

<script>
import { eventBus } from '../main.js'


export default {
  name: 'country-search',
  props: ['countrySearch'],
  methods: {
    handleClick(){
      eventBus.$emit('country-search', this.message)
    },
  },
  data(){
    return {
    message: null
  }
  }
}
</script>

<style lang="css" scoped>
</style>
