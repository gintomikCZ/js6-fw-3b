<template>
  <div v-if="show" class="modal-over" @click="clickOutside">
    <div class="modal" id="modalBody">
      <div class="modal-header">{{ header }}</div>
      <div class="modal-content">{{ content }}</div>
      <div class="modal-footer">
        <TButton :label="cancelButtonLabel" @clicked="onCancelClicked"/>
        <TButton :label="confirmButtonLabel" @clicked="onConfirmClicked"/>
      </div>
    </div>
  </div>
</template>

<script>
import TButton from '@/components/TButton.vue'

export default {
  name: 'TModal',
  props: {
    header: String,
    content: String,
    cancelButtonLabel: {
      type: String,
      default: 'cancel'
    },
    confirmButtonLabel: {
      type: String,
      default: 'OK'
    },
    show: {
      type: Boolean
    }
  },
  methods: {
    onCancelClicked() {
      this.$emit('cancelled')
    },
    onConfirmClicked() {
      this.$emit('confirmed')
    },
    clickOutside (event) {
      const modalBody = document.getElementById('modalBody')
      // pokud se nekliklo do těla modálu
      if (!modalBody.contains(event.target)) {
        this.$emit('close-me')
      }
      // jinak nic
    }
  },
  components: { TButton }
}
</script>

<style scoped>
.modal-over {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background: rgba(0, 0, 0, .15);
  display: flex;
  justify-content: center;
  align-items: center;
}
.modal {
  width: 300px;
  height: 200px;
  background: white;
  border-radius: 5px;
  box-shadow: 1px 1px 3px rgba(0, 0, 0, .2);
  display: flex;
  flex-direction: column;
}
.modal-header {
  flex-basis: 40px;
  flex-grow: 0;
  border-bottom: 1px solid #cdcdcd;
  padding: .35rem .7rem;
  display: flex;
  justify-content: center;
  align-items: center;
  font-weight: bold;
}
.modal-content {
  flex-grow: 1;
  padding: .35rem .7rem;
}
.modal-footer {
  padding: .35rem .7rem;
  flex-basis: 40px;
  flex-grow: 0;
  display: flex;
  border-top: 1px solid #cdcdcd;
  justify-content: flex-end;
  gap: .5rem;
}
</style>