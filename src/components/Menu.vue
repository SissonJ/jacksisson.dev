<script setup>
</script>

<template>
  <main>
    <div class="header-section" >
      <div class="header-text">
        Jack Sisson
      </div>
    </div>
    <div class="menu-section">
      <div class="menu-item">
        Photography
      </div>
      <div class="menu-item">
        Engineering
      </div>
      <div class="menu-item">
        Blog
      </div>
    </div>
  </main>
</template>

<style scoped>
main {
  background-color: #EFF0D1;
  color: #29335C;
  width: 100vw;
  height: 100vh;

  @media (min-width: 600px) {
    min-width: 600px;
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

      &:hover {
        font-size: 30px;
      }

      &:active {
        font-size: 30px;
      }
    }
  }

}
</style>
