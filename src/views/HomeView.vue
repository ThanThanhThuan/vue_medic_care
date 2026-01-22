<template>
  <main>
    <NavBar />
    <HeroSection />
    <AboutSection />
    <TimelineSection />
    <TestimonialsSection />
    <BookingSection />
  </main>
  <FooterSection />
</template>

<script setup>
import NavBar from '../components/NavBar.vue';
import HeroSection from '../components/HeroSection.vue';
import AboutSection from '../components/AboutSection.vue';
import TimelineSection from '../components/TimelineSection.vue';
import TestimonialsSection from '../components/TestimonialsSection.vue';
import BookingSection from '../components/BookingSection.vue';
import FooterSection from '../components/FooterSection.vue';
</script>

<style>
/* 
  Global styles are handled in index.html via css files in public/,
  but you can add specific Vue overrides here if needed.
*/
</style>