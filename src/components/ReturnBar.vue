<script setup>
const emits = defineEmits(['scroll-to-section']);

const emitIndex = (index) => {
  console.log("Scroll to section:", index);
  emits('scroll-to-section', index);
};
</script>

<template>
  <div @click="emitIndex(0)" class="return-bar">
    <span>^</span>
  </div>
</template>

<style scoped>
.return-bar {
  position: sticky;
  top: 0;
  width: 100vw;
  height: 40px;
  background-color: #30362F;
  color: #D7D9B1;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 24px;
  font-weight: 700;
  cursor: pointer;
  z-index: 1000;

  span {
    margin-top: 10px;
    font-size: 24px;
    font-weight: 700;
    color: #D7D9B1;
  }
}
</style>
