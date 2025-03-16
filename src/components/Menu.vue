<script setup>
const emits = defineEmits(['scroll-to-section']);

const emitIndex = (index) => {
  emits('scroll-to-section', index);
};
</script>

<template>
  <main>
    <div class="content-wrapper">
      <div class="header-section" >
        <div class="header-text">
          Jack Sisson
        </div>
      </div>
      <div class="menu-section">
        <div
          @click="emitIndex(1)"
          @touchend.prevent="emitIndex(1)"
          class="menu-item">
          Photography
        </div>
        <div 
          @click="emitIndex(2)"
          @touchend.prevent="emitIndex(2)"
          class="menu-item">
          Engineering
        </div>
        <div
          @click="emitIndex(3)"
          @touchend.prevent="emitIndex(3)"
          class="menu-item">
          Blog
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
main {
  background-color: #F2E8CF;
  color: #29335C;
  width: 100vw;
  height: 100vh;
  display: flex;
  align-items: center;
  flex-direction: column;

  .content-wrapper {
    width: 100%;

    @media (min-width: 600px) {
      max-width: 600px;
    }


    .header-section {
      display: flex;
      justify-content: left;
      align-items: center;
      margin-top: 100px;

      .header-text {
        font-size: 48px;
        font-weight: 700;
        margin: 30px;
      }
    }

    .menu-section {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: left;
      margin-top: 20px;

      .menu-item {
        font-size: 24px;
        font-weight: 600;
        margin: 30px;
        transition: font-size 0.3s ease-in-out;
        cursor: pointer;

        &:hover, &.touched {
          font-size: 30px;
        }
      }
    }
  }

}
</style>
