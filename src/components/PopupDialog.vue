<!-- PopupDialog.vue -->
<template>
  <div class="popup">
    <button @click="$emit('close')">Close</button>
    <ul>
      <li v-for="item in items" :key="item.code" @dblclick="selectItem(item)">
        {{ item.code }} - {{ item.name }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [
        { code: '코드1', name: 'Name1' },
        { code: '코드2', name: 'Name2' },
        { code: 'Code3', name: 'Name3' }
      ]
    };
  },
  methods: {
    selectItem(item) {
      this.$emit('select1', item); // 이벤트 이름 확인
    }
  }
};
</script>

<style>
.popup {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 50%;
  max-width: 600px;
  background: white;
  border: 1px solid #ccc;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
  padding: 20px;
  z-index: 1000;
}
</style>
