<template>
  <div>
    <div class="contact-item">
      <div class="contact-info">
        <div class="contact-container">
          <font-awesome-icon 
            :icon="['fas', 'user']" 
            class="icon-color"
          />
          <p>{{ contact.name }}</p>
        </div>
        <div class="contact-container">
          <font-awesome-icon 
          :icon="['fas', 'phone-alt']" 
          class="icon-color"
        />
          <p>{{ contact.phoneNumber }}</p>
        </div>
      </div>
      <button 
        class="del" 
        type="button" 
        @click="$emit('show-delete-modal', contact.id)"
      >
        <font-awesome-icon :icon="['fas', 'trash']" />
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
  margin: 0 15px 0 12px;
}

.contact-info {
  display: flex;
  flex-direction: column;
}
.contact-container {
  display: flex;
  flex-direction: row;
  align-items: center;
  margin-bottom: 6px;
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
  padding: 7px 9px;
  border-radius: 50%;
  cursor: pointer;
  font-weight: bolder;
  transition: 0.4s ease-out;
}
.del:hover {
  background: #cc0525;
}

.icon-color {
  color: whitesmoke;
}
</style>