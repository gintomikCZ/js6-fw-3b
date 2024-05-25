<template>
  <ul>
    <li v-for="country in countries">{{  country.country }}</li>
  </ul>
</template>

<script>

const documentClick = () => {
  console.log('document has been clicked')
}

export default {
  name: 'CountriesPage',
  props: {
    countries: Array
  },
  created () {
    document.addEventListener('click', documentClick)
  },
  beforeUnmount () {
    document.removeEventListener('click', documentClick)
  }
}


</script>