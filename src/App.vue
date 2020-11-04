<template>
  <div id="app">
    <Header 
      v-on:show-add-modal="renderAddModal"
    />
    <AddContact
      v-if="showAddModal" 
      v-on:show-add-modal="renderAddModal" 
      v-on:add-contact="addContact"
    />
    <Phonebook 
      v-bind:phonebook="phonebook"
      v-on:show-delete-modal="renderDeleteModal" 
    />
    <DeleteModal 
      v-if="showDeleteModal"
      v-on:show-delete-modal="renderDeleteModal"
      v-on:del-contact="deleteContact"
      v-bind:deleteId="deleteId"
    />
  </div>
</template>

<script>
import Header from './components/layout/Header';
import Phonebook from './components/Phonebook';
import AddContact from './components/AddContact';
import DeleteModal from './components/DeleteModal';

export default {
  name: 'App',
  components: {
    Header,
    Phonebook,
    AddContact,
    DeleteModal
  },
  data() {
    return {
      showAddModal: false,
      showDeleteModal: false,
      deleteId: null,
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
    addContact(newContact) {
      this.phonebook = [newContact, ...this.phonebook];
    },
    deleteContact(id) {
      this.phonebook = this.phonebook.filter(contact => contact.id !== id);
      this.showDeleteModal = false;
      this.deleteId = null;
    },
    renderAddModal() {
      this.showAddModal = !this.showAddModal;
    },
    renderDeleteModal(id) {
      this.showDeleteModal = !this.showDeleteModal;
      if (id) {
        this.deleteId = id;
      }
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
  font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif, Helvetica;
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

.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: table;
  transition: opacity 0.3s ease;
}

.modal-wrapper {
  display: table-cell;
  vertical-align: middle;
}
</style>
