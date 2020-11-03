<template>
  <div id="app">
    <Header />
    <AddContact v-on:add-contact="addContact" />
    <Phonebook 
      v-bind:phonebook="phonebook"
      v-on:del-contact="deleteContact" 
    />
  </div>
</template>

<script>

import Header from './components/layout/Header';
import Phonebook from './components/Phonebook';
import AddContact from './components/AddContact'

export default {
  name: 'App',
  components: {
    Header,
    Phonebook,
    AddContact
  },
  data() {
    return {
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
}

.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 2px;
  cursor: pointer;
}

.btn:hover {
  background: #666;
}

</style>
