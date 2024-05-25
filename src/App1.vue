<template>
  <h1>bubák application</h1>
  <div>
    <TButton label="ukaž bubáka" @clicked="onClicked" :isDisabled="showBubak" />

  </div>
  <div class="container" v-if="showBubak">
    <TPicture header="tohle je bubák" source="/src/assets/bubak.jpg" @close-me="onCloseMe" />
  </div>
  <TModal :show="showModal" header="warning!!!" content="ty chceš fakt vidět bubáka??" @cancelled="showModal = false"
    @confirmed="onConfirmed" @close-me="showModal = false"/>
</template>

<script>
import TButton from '@/components/TButton.vue'
import TPicture from '@/components/TPicture.vue'
import TModal from '@/components/TModal.vue'
  export default {
    name: 'App',
    data () {
      return {
        showBubak: false,
        showModal: false
      }
    },
    methods: {
      onClicked () {
        this.showModal = true
      },
      onCloseMe () {
        this.showBubak = false
      },
      onConfirmed () {
        this.showModal = false
        this.showBubak = true
      },
    },
    components: { TButton, TPicture, TModal }
  }

</script>
<style scoped>
.container {
  margin-top: 2rem;
}
</style>