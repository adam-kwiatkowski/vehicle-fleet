<template>
  <transition name="modal">
    <div class="modal-mask">
      <div class="modal-wrapper" @click="$emit('close')">
        <div class="modal-dialog" @click.stop>
          <div class="modal-content">
            <div class="modal-header">
              <h5 class="modal-title">{{ title }}</h5>
              <button
                type="button"
                class="btn-close"
                @click="$emit('close')"
              ></button>
            </div>
            <div class="modal-body">
              <slot name="body"></slot>
            </div>
            <div class="modal-footer">
              <slot name="footer"></slot>
            </div>
          </div>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  props: ["title"],
};
</script>

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

.modal-dialog {
  transition: all 0.3s ease;
}

.modal-enter-active {
  opacity: 0;
}

.modal-leave-active {
  opacity: 0;
}

.modal-enter .modal-dialog,
.modal-leave-active .modal-dialog {
  -webkit-transform: scale(1.05);
  transform: scale(1.05);
}
</style>