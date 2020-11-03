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
      <div class="buttonContainer">
        <button type="submit" class="btn">
          Submit
        </button>
        <button type="button" class="btn" @click="$emit('show-modal', false)"> 
          Cancel
        </button>
      </div>
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
      this.$emit('show-modal', false);

      this.name = '';
      this.phoneNumber = '';
    }
  }  
}
</script>

<style scoped>
  .formContainer {
    padding: 30px;
    border-radius: 15px;
    width: 310px;
    background: #20232a;
    margin-left: auto;
    margin-right: auto;
  }

  form {
    display: flex;
    flex-direction: column;
    width: 100%;
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
    color: whitesmoke;
  }

  .btn {
    font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif, Helvetica;
  }

  .buttonContainer {
    display: flex;
    flex-direction: row;
  }
</style>