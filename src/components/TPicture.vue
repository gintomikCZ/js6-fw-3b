<template>
  <div class="container">
    <div class="top">
      <div class="header">{{ header }}</div>
      <div class="close-btn" @click="onClick">X</div>
    </div>
    <div>
      <TButton :label="blured ? 'unblur' : 'blur'"  @clicked="blured=!blured"/>
    </div>
    <div class="main" :class="{'is-blured': blured}">
      <img :src="source" />
    </div>
  </div>
</template>

<script>
import TButton from './TButton.vue';
export default {
  name: 'TPicture',
  data () {
    return {
      blured: true
    }
  },
  props: {
    header: String,
    source: String
  },
  methods: {
    onClick() {
      this.$emit('close-me')
    }
  },
  components: {TButton}
}

</script>
<style scoped>
  .container {
    border: 1px solid #cdcdcd;
  }
  .header {
    padding: 1rem;
    font-weight: bold;
  }
  .top {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background: pink;
    color: black
  }
  .close-btn {
    padding: 1rem;
    cursor: pointer;
  }
  .close-btn:hover {
    background: lightpink
  }
  .main {
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 1rem;
  }
  .is-blured {
    filter: blur(10px)
  }
</style>