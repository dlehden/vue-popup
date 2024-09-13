<!-- MainComponent.vue -->
<template>
  <div>
    <button @click="openPopup">Open Popup</button>
    <p>Selected Code: {{ selectedCode }} - {{ selectedName }}</p>
    <div v-if="isPopupOpen" class="popup-overlay" @click="isPopupOpen = false"></div>
    <PopupDialog
      v-if="isPopupOpen"
      @close="isPopupOpen = false"
      @select1="handleSelect" 
    />
  </div>
</template>

<script>
import PopupDialog from './PopupDialog.vue'; // 컴포넌트 경로 확인

export default {
  components: {
    PopupDialog
  },
  data() {
    return {
      isPopupOpen: false,
      selectedCode: '',
      selectedName: ''
    };
  },
  methods: {
    openPopup() {
      this.isPopupOpen = true;
    },
    handleSelect({ code, name }) {
      this.selectedCode = code;
      this.selectedName = name;
      this.isPopupOpen = false;
    }
  }
};
</script>

<style>
.popup-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  z-index: 999;
}
</style>
