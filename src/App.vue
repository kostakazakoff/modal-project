<template>
  <div>

    <h1>{{title}}</h1>
    <br>
    <button @click="toggleModal">show modal</button>
    <br>
    <button @click="toggleModalTwo">show second modal</button>

    <teleport to="#modals" v-if="showModal">
      <Modal theme="sa" @close-modal="toggleModal">
        <template v-slot:links>
          <a href="#">Sign Up Now</a>
          <a href="#">More Info</a>
        </template>
        <h1>Modal Header</h1>
        <p>Modal Text</p>
      </Modal>
    </teleport>

    <teleport to="#modals" v-if="showModalTwo">
      <Modal @close-modal="toggleModalTwo">
        <template v-slot:links>
          <a href="#">Sign Up Now</a>
          <a href="#">More Info</a>
        </template>
        <h1>Second Modal</h1>
        <p>Second Modal Text</p>
      </Modal>
    </teleport>

  </div>
</template>

<script>
import Modal from "./components/Modal.vue";

export default {
  name: "App",
  components: { Modal },
  data() {
    return {
      title: "My First Vue.js App",
      showModal: false,
      showModalTwo: false
    };
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name.value);
    },
    toggleModal() {
      this.showModal = !this.showModal;
    },
    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo;
    }
  }
};
</script>

<style>
#app,
#modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  display: inline-block;
  padding-bottom: 10px;
}
button {
  padding: 8px 16px;
  margin: 10px;
  border: none;
}
</style>
