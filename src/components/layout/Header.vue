<template>
  <header class="header">
    <h3>Phonebook</h3>
    <button 
      class="plus" 
      type="button" 
      @click="$emit('show-add-modal')"
    >
      <font-awesome-icon :icon="['fas', 'plus']" />
    </button>
  </header>
</template>

<script>
export default {
  name: "Header"
}
</script>

<style scoped>
  .header {
    background: #323a41;
    color: #fff;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    padding: 10px 20px 10px 20px;
  }

  .plus {
    background: #007bfe;
    color: #fff;
    border: none;
    padding: 7px 9px;
    border-radius: 50%;
    cursor: pointer;
    font-weight: bolder;
    transition: 0.4s ease-out;
  }
  .plus:hover {
    background: #00b5fe;
  }
</style>