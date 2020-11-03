<template>
  <div id="app">
    <Header 
      v-on:show-modal="renderModal"
    />
    <AddContact 
      v-on:add-contact="addContact"
      v-on:show-modal="renderModal" 
      v-if="showModal"
    />
    <Phonebook 
      v-bind:phonebook="phonebook"
      v-on:del-contact="deleteContact" 
    />
  </div>
</template>

<script>

import Header from './components/layout/Header';
import Phonebook from './components/Phonebook';
import AddContact from './components/AddContact';

export default {
  name: 'App',
  components: {
    Header,
    Phonebook,
    AddContact
  },
  data() {
    return {
      showModal: false,
      phonebook: [
        {
          id: 1,
          name: 'Elliot',
          phoneNumber: '310-311-3131'
        },
        {
          id: 2,
          name: 'Andrew',
          phoneNumber: '210-211-2121'
        },
        {
          id: 3,
          name: 'David',
          phoneNumber: '410-411-4141'
        },
      ]
    }
  },
  methods: {
    deleteContact(id) {
      this.phonebook = this.phonebook.filter(contact => contact.id !== id);
    },
    addContact(newContact) {
      this.phonebook = [newContact, ...this.phonebook];
    },
    renderModal() {
      this.showModal = !this.showModal;
    }
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif, Helvetica;
  line-height: 1.4;
  background: #323a41;
}

.btn {
  display: inline-block;
  border: none;
  background: #2fc05f;
  border-radius: 10px;
  color: #fff;
  padding: 7px 2px;
  cursor: pointer;
  margin-top: 15px;
  width: 30%;
  margin-left: auto;
  margin-right: auto;
  transition: 0.4s ease-out;
}
.btn:hover {
  background: #1e7e26;
}

.modal-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 98;
  width: 100vw;
  height: 100vh;
  background-color: rgba(0, 0, 0, 0.1);
}
</style>
