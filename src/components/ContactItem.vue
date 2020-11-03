<template>
  <div>
    <div class="contact-item">
      <div class="contact-info">
        <p>{{ contact.name }}</p>
        <p>{{ contact.phoneNumber }}</p>
      </div>
      <button 
        class="del" type="button" 
        @click="$emit('show-delete-modal', contact.id)"
      >
        x
      </button>
    </div>
    <div class="line"></div>
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
    padding: 10px 40px 10px 20px;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
  }

  p {
    color: #c3c5c6;
    margin-right: 15px;
  }

  .contact-info {
    display: flex;
    flex-direction: column;
  }

  .line {
    width: 250px;
    border-bottom: 1px solid whitesmoke;
    border-bottom-width: thin;
    margin: 0 0 0 20px;
  }

  .del {
    background: #f41f41;
    color: #fff;
    border: none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
    font-weight: bolder;
    transition: 0.4s ease-out;
  }
  .del:hover {
    background: #cc0525;
  }
</style>