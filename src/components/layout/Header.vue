<template>
  <header class="header">
    <h3>Contacts</h3>
    <button 
      class="plus" type="button" 
      @click="$emit('del-contact', contact.id)"
    >
      +
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

  .header a {
    color: #fff;
    padding-right: 5px;
  }

  .plus {
    background: #007bfe;
    color: #fff;
    border: none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
    font-weight: bolder;
  }
</style>