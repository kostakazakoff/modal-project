<template>
  <div>
    <h1>{{title}}</h1>
    <button @click="toggleModal">show modal</button>
    <div v-if="showModal">
      <Modal
        :header="header"
        :text="text"
        theme="sale"
        showModal="showModal"
        @close-modal="toggleModal"
      />
    </div>
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
      header: "Sign in",
      text: "Please enter your credentials",
      showModal: false
    };
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name.value);
    },
    toggleModal() {
      this.showModal = !this.showModal;
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
