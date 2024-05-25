<template>
  <button @click="onClick" :disabled="isDisabled">{{  label  }}</button>
</template>

<script>

export default {
  name: 'TButton',
  props: {
    label: String,
    isDisabled: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    onClick(e) {
      e.stopPropagation()
      this.$emit('clicked')
    }
  }
}

</script>

<style scoped>
button:disabled {
  cursor: not-allowed;
  background: white;
  border: none;
}
</style>