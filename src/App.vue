<!--
Modal component with customizable slots and CSS transitions.
-->

<script>
import Modal from './components/ModalComponent.vue'

export default {
  components: {
    Modal
  },
  data() {
    return {
      showModal: false,
      text : 'Text',
      headerText:'Header',
      Footer:'Footer'
    }
  }
}
</script>

<template>
  <div class="root">
    <h3>HeaderText</h3>
    <input v-model="headerText">
    <h3>Text</h3>
    <input v-model="text">
    <br>
    <h3>Footer</h3>
    <input v-model="Footer">
    <br>

    <button class="btn" id="show-modal" @click="showModal = true">Show Modal</button>

    <!--  <input v-model="header">-->
    <Teleport to="body">
      <!-- use the modal component, pass in the prop -->
      <modal :footer="Footer" :header="headerText" :text="text" :show="showModal" @close="showModal = false">
        <template #header>
          <h3>{{ headerText }}</h3>
        </template>
      </modal>
    </Teleport>
  </div>

</template>

<style>
button{
  cursor:pointer;
}
.btn{
  transition: 0.3s;
  margin: 10px;
  padding: 10px 20px;
  background: bottom;
  border-radius: 10px;
}
.btn:hover{

  background-color: #deb0b0;
  cursor: pointer;
  border-color: #939296;
}
.btn{
  margin: 30px;
}
.root{
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>