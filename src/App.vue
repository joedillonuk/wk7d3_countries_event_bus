<template>
  <div>
    <h1>Countries</h1>
    <div>
      <h2>Select a country:</h2>
      <country-select :countries='countries'></country-select>
      <country-detail :country='selectedCountry'></country-detail>
      <h2>Search country by name:</h2>
      <country-search :countrySearch='countrySearch'></country-search>
      <countries-list :countrySearch='countrySearch'></countries-list>
    </div>
  </div>
</template>

<script>
import CountriesList from './components/CountriesList.vue';
import CountryDetail from './components/CountryDetail.vue';
import CountrySelect from './components/CountrySelect.vue';
import CountrySearch from './components/CountrySearch.vue';


import { eventBus } from './main.js'
export default {
  name: 'app',
  data(){
    return {
      countries: [],
      countrySearch: [],
      selectedCountry: null
    };
  },
  mounted(){
    fetch('https://restcountries.eu/rest/v2/all')
    .then(res => res.json())
    .then(countries => this.countries = countries)

    eventBus.$on('country-selected', (country) => {
      this.selectedCountry = country
    }),
    eventBus.$on('country-search', (search) => {
      fetch(`https://restcountries.eu/rest/v2/name/${search}`)
      .then(res => res.json())
      .then(countrySearch => this.countrySearch = countrySearch)
    })

  },
  components: {
    "countries-list": CountriesList,
    "country-detail": CountryDetail,
    "country-select": CountrySelect,
    "country-search": CountrySearch
  }

}
</script>

<style>
.main-container {
  display: flex;
  justify-content: space-between;
}
</style>
