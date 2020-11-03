<template>
  <div class="contact-item">
    <div class="contact-info">
      <p>{{ contact.name }}</p>
      <p>{{ contact.phoneNumber }}</p>
    </div>
    <button 
      class="del" type="button" 
      @click="$emit('del-contact', contact.id)"
    >
      x
    </button>
  </div>
</template>

<script>
export default {
  name: "ContactItem",
  props: ["contact"]
}
</script>

<style scoped>
  .contact-item {
    background: #f4f4f4;
    padding: 10px;
    border-bottom: 1px #ccc dotted;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
  }

  .contact-info {
    display: flex;
    flex-direction: row;
  }

  p {
    margin-right: 15px;
  }

  .del {
    background: #ff0000;
    color: #fff;
    border: none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
  }
</style>