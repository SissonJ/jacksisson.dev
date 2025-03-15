<script setup>
</script>

<template>
  <main>
    <div class="content-wrapper">
      <div class="header-section" >
        <div class="header-text">
          Engineering
        </div>
      </div>
      <div class="menu-section">
        <div class="menu-item">
          Coming Soon :)
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
main {
  background-color: #D6EEFF;
  color: #3E442B;
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
      margin-top: 50px;

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
      }
    }
  }
}
</style>
