<template>
  <div class="formContainer">
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
  .formContainer {
    padding: 15px;
    border-top-left-radius: 15px;
    border-top-right-radius: 15px;
    background: #20232a;
  }

  form {
    display: flex;
    flex-direction: column;
    width: 35%;
    margin-left: auto;
    margin-right: auto;
  }

  input[type="text"] {
    padding: 5px;
    font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif, Helvetica;
    background: #20232a;
    border: none;
    border-bottom: 2px solid whitesmoke;
    margin-bottom: 5px;
  }

  .btn {
    font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif, Helvetica;
  }
</style>