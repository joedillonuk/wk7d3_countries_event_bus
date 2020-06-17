<template lang="html">
  <div>
    <div v-if='countrySearch.status'>
      <h2>Sorry, no results.</h2>
    </div>
    <div v-if='!countrySearch.status'>
    <ul>
      <list-item v-for="(country, index) in countrySearch" :country="country" :key="index"></list-item>
    </ul>
    </div>
  </div>
</template>

<script>
import ListItem from './ListItem.vue';

export default {
  name: 'countries-list',
  props: ['countrySearch'],
  components: {
    "list-item": ListItem
  }
}
</script>

<style lang="css" scoped>
</style>
