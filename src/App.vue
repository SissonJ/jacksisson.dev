<script setup>
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <!--<header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />
    </div>
  </header>-->

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
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}

html, body, #app {
  height: 100vh;
  width: 100vw;
  margin: 0;
  padding: 0;
  background-color: #f8ede2;
  display: flex;
  justify-content: center;
  align-items: center;
}

main {
  background-color: #f8ede2;
  color: black;
  width: 100vw;
  height: 100vh;

  .header-section {
    display: flex;
    justify-content: left;
    align-items: center;
    margin-top: 100px;

    .header-text {
      font-size: 34px;
      font-weight: 700;
      margin: 30px;
    }
  }

  .menu-section {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: left;
    margin-top: 50px;

    .menu-item {
      font-size: 24px;
      font-weight: 600;
      margin: 30px;

      &:hover {
        font-size: 27px;
      }
    }
  }

}
</style>
