<template lang="html">
  <div>
    <select v-on:change="handleChange" v-model="selected">
      <option disabled value="">Select a country</option>
      <option v-for="(country, index) in countries" :country="country" :key="index" v-bind:value="country">{{country.name}}</option>
    </select>
  </div>
</template>

<script>
import { eventBus } from '../main.js'


export default {
  name: 'country-select',
  props: ['countries'],
  methods: {
    handleChange(){
      eventBus.$emit('country-selected', this.selected)
    },
  },
  data(){
    return {
    selected: null,
  }
  }
}
</script>

<style lang="css" scoped>
</style>
