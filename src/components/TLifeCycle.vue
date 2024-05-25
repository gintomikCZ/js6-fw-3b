<template>
  <div>i am lifecycle demo component</div>
</template>

<script>

export default {
  name: 'TLifeCycle',
  beforeCreate () {
    console.log('before create')
  },
  created () {
    console.log('created')
  },
  beforeMount () {
    console.log('before mount')
  },
  mounted () {
    console.log('mounted')
  },
  beforeUnmount () {
    console.log('before unmount')
  },
  unmounted () {
    console.log('unmounted')
  }

}

</script>