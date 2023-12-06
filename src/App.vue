<template>
  <!-- showing the modal based on the showModal boolean -->
  <!-- teleport component to place this in a div in index.html with id modal -->
  <teleport to="#modal" v-if="showModal">
    <!-- in case we want to use slots we use both the opening and closing tag not just self-closing -->
    <!-- passing the prop theme for the dynamic class and a custom event 'close' to close the modal on backdrop click -->
    <Modal theme="sale" @close="toggleModal">
      <!-- custom slot -->
      <template v-slot:links>
        <a href="#">Dajj</a>
        <a href="#">Gaaaa</a>
      </template>
      <!-- this gets passed into the default slot -->
      <h1>OJJJJJ</h1>
      <p>YOOOOOO</p>
    </Modal>
  </teleport>

  <teleport to="#modal" v-if="showModal2">
    <!-- passing the prop theme and custom event close to toggle the modal -->
    <Modal theme="nistaaa" @close="toggleModal2">
      <!-- custom slot -->
      <template v-slot:links>
        <a href="#">Opppa</a>
        <a href="#">Modal Dvaaa</a>
      </template>
    </Modal>
  </teleport>
  <!-- toggle the showModal if the button is clicked with alt (opens), toggle if the backdrop is clicked(closes it) -->
  <button @click.alt="toggleModal">open modal with alt</button>
  <!-- same thing just with normal click (no modifiers) and opens second modal-->
  <button @click="toggleModal2">open modal 2</button>
</template>

<script>
import Modal from './components/Modal.vue';

export default {
  name: 'App',
  components: {
    Modal
  },
  data() {
    return {
      showModal: false,
      showModal2: false
    }
  },
  methods: {
    toggleModal() {
      this.showModal = !this.showModal;
    },
    toggleModal2() {
      this.showModal2 = !this.showModal2;
    }
  }
}
</script>

<style>
#app,
#modal {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
