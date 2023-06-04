<template>
  <h1>{{ title }}</h1>
  <input type="text" ref="name">
  <button @click="handleClick">click me</button>
  <br>
  <teleport to=".modals" v-if="showModal">
    <Modal theme="sale" @close="toggleModal">
      <template v-slot:links>
        <a href="#">sign up now</a>
        <a href="#">more info</a>
      </template>
      <h1>{{ header }}</h1>
      <p>{{ text }}</p>
    </Modal>
  </teleport>
  <br>

  <div v-if="showModalTwo">
    <Modal theme="sale" @close="toggleModalTwo">
      <template v-slot:links>
        <a href="#">Try Again</a>
      </template>

      <h1>New Modal!</h1>
      <p>Lorem ipsum, dolor sit amet consectetur adipisicing elit. Magni id recusandae qui quo error pariatur dolore
        repellat earum veritatis ut? Rem quaerat accusamus asperiores laudantium laborum molestiae illo minus quasi.</p>
    </Modal>
  </div>

  <button @click="toggleModal">Open modal A</button>
  <br>
  <br>

  <button @click="toggleModalTwo">Open modal 2</button>
</template>

<script>
import Modal from './components/Modal'

export default {
  name: "App",
  components: {
    Modal
  },
  data() {
    return {
      title: "My First Vue App",
      header: "Ninja GiveWay",
      text: "Grab your ninja swag for half",
      showModal: false,
      showModalTwo: false,
    }
  },

  methods: {
    handleClick() {
      this.$refs.name.classList.toggle('active')
      this.$refs.name.focus()
    },

    toggleModal() {
      this.showModal = !this.showModal
    },

    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo
    }
  }
}
</script>

<style>
#app,
.modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1 {
  border-bottom: 1px solid #ddd;
  padding-bottom: 10px;
}
</style>