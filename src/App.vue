<template>
  <main>
    <NavBar />
    
    <!-- This switches between HomeView and AdminView -->
    <router-view />

  </main>
  <FooterSection />
</template>

<script setup>
import NavBar from './components/NavBar.vue';
import FooterSection from './components/FooterSection.vue';
import { onMounted } from 'vue';

onMounted(() => {
  // Re-inject custom scripts if needed for carousel
  const script = document.createElement("script");
  script.src = "/js/custom.js";
  script.async = true;
  document.body.appendChild(script);
});
</script>