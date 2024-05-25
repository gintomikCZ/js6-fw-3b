<template>
  <TButton label="get it out" @clicked="loading = !loading"/>
  <!-- <h1>ahoj</h1>
  <TButton @clicked="show = !show" label="show"/>
  <TLifeCycle v-if="show" /> -->
  <TLoading v-if="loading" />
  <CountriesPage v-else :countries="countries"/>
</template>

<script>
import TLifeCycle from './components/TLifeCycle.vue'
import TButton from './components/TButton.vue'
import TLoading from './components/TLoading.vue'
import CountriesPage from './components/CountriesPage.vue'
import { getCountries } from './data/countries.js'

export default {
  name: 'App',
  data () {
    return {
      show: false,
      loading: true,
      countries: null
    }
  },
  created () {
    getCountries().then(data => {
      this.countries = data
      this.loading = false
      console.log('data loaded')
    })

  },
  mounted () {
    console.log('mounted')
  },
  components: { TLifeCycle, TButton, CountriesPage, TLoading }
}


</script>