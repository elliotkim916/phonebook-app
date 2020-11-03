<template>
  <div>
    <form @submit.prevent="addContact">
      <input 
        type="text" 
        name="name" 
        v-model="name" 
        placeholder="Enter name.."
        required
      >
      <input 
        type="text" 
        name="phoneNumber" 
        v-model="phoneNumber" 
        placeholder="Enter phone number.."
        required
      >
      <input type="submit" value="Submit" class="btn">
    </form>
  </div>
</template>

<script>
import { v4 as uuidv4 } from 'uuid';

export default {
  name: "AddContact",
  data() {
    return {
      name: '',
      phoneNumber: ''
    }
  },
  methods: {
    addContact() {
      const newContact = {
        id: uuidv4(),
        name: this.name,
        phoneNumber: this.phoneNumber 
      };

      // send up to parent
      this.$emit('add-contact', newContact);

      this.name = '';
      this.phoneNumber = '';
    }
  }  
}
</script>

<style scoped>
  form {
    display: flex;
  }

  input[type="text"] {
    flex: 10;
    padding: 5px
  }

  .btn {
    flex: 2;
  }
</style>