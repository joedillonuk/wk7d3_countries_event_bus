<template lang="html">
<div v-if='country'>
  <h3>{{country.name}}</h3>
  <p><b>Capital:</b> {{country.capital}}</p>
  <p><b>Population:</b> {{country.population}}</p>
  <h3>Languages</h3>
  <p v-for="(language, index) in country.languages" :language="language" :key="index">{{language.name}}</p>
<h3>Flag:</h3>
  <img :src="country.flag" alt="Flag" width="250" height="150">

</div>


</template>

<script>
export default {
  name: 'country-detail',
  props: ['country'],
  data(){
    return{
      language: null,
      key: null
    }
  }
}
</script>

<style lang="css" scoped>
</style>
