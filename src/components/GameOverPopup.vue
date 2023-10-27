<script>
export default {
  props: {
    show: Boolean
  },
}
</script>

<template>
  <Transition name="modal">
    <div v-if="show" class="modal-mask">
      <div class="modal-wrapper">
        <div class="modal-container">
          <div class="modal-header">
            <slot name="outputWinner"></slot>
          </div>

                <section class="button-section">
              <button
                class="modal-default-button"
                @click="$emit('new-game')"
              >Restart game</button>
              
                </section>
          </div>
        </div>
      </div>
  </Transition>
</template>

<style scoped>
.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: table;
  transition: opacity 0.3s ease;
}

.modal-wrapper {
  display: table-cell;
  vertical-align: middle;
  
}

.modal-container {
  width: 300px;
  margin: 0px auto;
  padding: 20px 30px;
  background-color: #fff;
  border-radius: 2px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
  transition: all 0.3s ease;
  width: 300px;
  min-height: 150px;
  text-align: center;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
.button-section{
    margin: 0 auto;
    display: flex;
    flex-direction: column;
    gap: 10px;
}
.modal-header h3 {
  margin-top: 0;
  font-size: 32px;
  text-align: center;
}

.modal-body {
  margin: 20px 0;
}



.modal-default-button {
  float: right;
}

button {
  width: 7rem;
  height: 2.5rem;
  padding: auto;
  font-size: 0.8rem;
  cursor: pointer;
  background-color: rgb(203, 0, 0);
  color: #fff;
  border-radius: 15px;
  border: 1px solid rgb(203, 0, 0);
  margin: 0 auto;
}

button:hover {
  background-color: rgb(203, 30, 0);
}
.modal-enter-from {
  opacity: 0;
}

.modal-leave-to {
  opacity: 0;
}

.modal-enter-from .modal-container,
.modal-leave-to .modal-container {
  -webkit-transform: scale(1.1);
  transform: scale(1.1);
}
</style>