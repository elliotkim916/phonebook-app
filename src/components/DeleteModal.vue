<template>
  <transition name="modal">
    <div class="modal-mask">
      <div class="modal-wrapper"> 
        <div class="modal-container">
          <h3>Are you sure you want to delete this contact?</h3>
          <div class="btn-container">
            <button 
              @click="$emit('del-contact', deleteId)" 
              class="btn"
            >
              YES
            </button>
            <button 
              @click="$emit('show-delete-modal')" 
              class="btn"
            >
              NO
            </button>
          </div>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  name: "DeleteModal",
  props: ['deleteId']
}
</script>

<style scoped>
.modal-container {
  padding: 30px;
  border-radius: 15px;
  width: 310px;
  background: #20232a;
  margin-left: auto;
  margin-right: auto;
  color: whitesmoke;
}

.btn-container {
  display: flex;
  flex-direction: row;
}
</style>