<template>
  <div class="phonebookContainer">
    <div 
      v-for="contact in phonebook" 
      v-bind:key="contact.id"
    >
      <ContactItem 
        v-bind:contact="contact" 
        v-on:del-contact="$emit('del-contact', contact.id)" 
      />
    </div>
  </div>
</template>

<script>
import ContactItem from './ContactItem.vue';

export default {
  name: 'Phonebook',
  components: {
    ContactItem
  },
  props: ["phonebook"]
}
</script>

<style scoped>
  .phonebookContainer {
    width: 300px;
    position: absolute;
    top: 50%;
    left: 50%;
    -webkit-transform: translate(-50%, -50%);
    transform: translate(-50%, -50%);
  }
</style>