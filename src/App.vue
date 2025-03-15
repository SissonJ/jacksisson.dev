<script setup>
import Blog from './components/Blog.vue';
import Engineering from './components/Engineering.vue';
import Menu from './components/Menu.vue';
import Photography from './components/Photography.vue';
import { ref, onMounted, onUnmounted, nextTick, watch } from "vue";
import ReturnBar from './components/ReturnBar.vue';

// Section data
const sections = ref([
  { title: "Menu" },
  { title: "Photography" },
  { title: "Engineering" },
  { title: "Blog" },
]);

const sectionRefs = ref([]);

// Ensure Vue correctly detects all refs after render
onMounted(async () => {
  await nextTick(); // Ensures refs are populated
  sectionRefs.value = document.querySelectorAll("section");
});

const currentIndex = ref(0);

// Scroll to a specific section
watch(currentIndex, (index) => {
  console.log(sectionRefs.value);
  if (sectionRefs.value[index]) {
    sectionRefs.value[index].scrollIntoView({ behavior: "smooth" });
  }
});

const debounce = (fn, delay) => {
  let timeoutId;
  return (...args) => {
    if (timeoutId) clearTimeout(timeoutId);
    timeoutId = setTimeout(() => fn(...args), delay);
  };
};

// Handle wheel scrolling (Desktop)
const handleScroll = debounce((event) => {
  if (event.deltaY > 0 && currentIndex.value < sections.value.length - 1) {
    currentIndex.value++;
  } else if (event.deltaY < 0 && currentIndex.value > 0) {
    currentIndex.value--;
  }
  event.preventDefault();
}, 100);

// Touch swipe detection (Mobile)
let touchStartY = 0;

const handleTouchStart = (event) => {
  touchStartY = event.touches[0].clientY;
};

const handleTouchEnd = (event) => {
  const touchEndY = event.changedTouches[0].clientY;
  const deltaY = touchStartY - touchEndY;

  if (deltaY > 50 && currentIndex.value < sections.value.length - 1) {
    debounce(() => currentIndex.value++, 100)();
  } else if (deltaY < -50 && currentIndex.value > 0) {
    debounce(() => currentIndex.value--, 100)();
  }
  event.preventDefault();
};

// Dynamically return components
const getComponent = (title) => {
  switch (title) {
    case 'Menu': return Menu;
    case 'Photography': return Photography;
    case 'Engineering': return Engineering;
    case 'Blog': return Blog;
    default: return null;
  }
};

const emitHandler = (index) => {
  console.log('HERE');
  currentIndex.value = index;
};

onMounted(() => {
  window.addEventListener("wheel", handleScroll, { passive: false });
  document.addEventListener("touchstart", handleTouchStart, { passive: false });
  document.addEventListener("touchend", handleTouchEnd, { passive: false });
});

onUnmounted(() => {
  window.removeEventListener("wheel", handleScroll);
  document.removeEventListener("touchstart", handleTouchStart);
  document.removeEventListener("touchend", handleTouchEnd);
});
</script>
<template>
  <div class="page-container">
    <section 
      v-for="(section, index) in sections.slice(0, 1)" 
      :key="index"
      ref="sectionRefs"
    >
      <component :is="getComponent(section.title)" @scroll-to-section="emitHandler" />
    </section>
    <ReturnBar @scroll-to-section="emitHandler" />
    <section 
      v-for="(section, index) in sections.slice(1)" 
      :key="index + 1"
      ref="sectionRefs"
    >
      <component :is="getComponent(section.title)" />
    </section>
  </div>
</template>
<style scoped>
.page-container {
  height: 100vh;
  overflow: hidden; /* Prevents unwanted scrolling */
}

section {
  height: 100vh;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  transition: transform 0.5s ease-in-out;
}
</style>

