<script setup>
import {Photos} from '@/lib/photos';
import { onMounted, ref } from 'vue';

const index = ref(0);

const currentPhoto = ref(null);

const photos = Object.values(Photos).map(photo => {
  return {
    src: new URL(photo, 'https://jacksisson.dev/api/photo/'),
  };
});


const movePhotoForward = () => {
  index.value = (index.value + 1) % photos.length;
  currentPhoto.value = photos[index.value].src;
  const next = new Image();
  next.src = photos[(index.value + 1) % photos.length].src;
};

const movePhotoBackward = () => {
  index.value = (index.value - 1) % photos.length;
  if (index.value === -1) {
    index.value = photos.length - 1;
  }
  currentPhoto.value = photos[index.value].src;
  if (index.value !== 0) {
    const next = new Image();
    next.src = photos[index.value - 1 % photos.length].src;
  } else {
    const next = new Image();
    next.src = photos[photos.length - 1].src;
  }
};


onMounted(() => {
  index.value = Math.floor((Math.random() * 100) + 1);
  const img = new Image();
  img.src = photos[index.value % photos.length].src;
  img.onload = () => {
    currentPhoto.value = img.src;
  };
  const next = new Image();
  next.src = photos[index.value + 1 % photos.length].src;
});

</script>
<template>
  <main>
    <div class="content-wrapper">
      <div class="header-section" >
        <div class="header-text">
          Photography
        </div>
      </div>
      <div class="photography-section">
        <div class="scroll-button" 
          @click="movePhotoBackward"
          @touchend.prevent="movePhotoBackward"
        > O </div>
        <img :src="currentPhoto">
        <div class="scroll-button" 
          @click="movePhotoForward"
          @touchend.prevent="movePhotoForward"
        > O </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
main {
  background-color: #D7D9B1;
  color: #30362F;
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
      padding: 50px 10px 0;

      .header-text {
        font-size: 48px;
        font-weight: 700;
        margin: 30px;
      }
    }

    .photography-section {
      display: flex;
      justify-content: center;
      align-items: center;
      background-color: #5B85AA;
      padding: 20px 0;
      border-radius: 10px;
      max-height: 38vh;

      .scroll-button {
        display: flex;
        justify-content: center;
        align-items: center;
        cursor: pointer;
        font-size: 24px;
        font-weight: 600;
        margin: 0 5px;
        color: #D7D9B1;
      }

      img {
        width: 100%;
        height: auto;
        max-width: 85%;
        object-fit: cover;
      }
    }
  }

}
</style>
