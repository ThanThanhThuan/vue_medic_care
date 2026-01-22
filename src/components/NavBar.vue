<template>
  <nav class="navbar navbar-expand-lg bg-light fixed-top shadow-lg">
    <div class="container">
      <router-link class="navbar-brand mx-auto d-lg-none" to="/">
        THAN's Medic Care
        <strong class="d-block">Health Specialist</strong>
      </router-link>

      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>

      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav mx-auto">
          
          <!-- HOME PAGE LINKS (Only show if on Home) -->
          <template v-if="route.path === '/'">
            <li class="nav-item active">
              <a class="nav-link" href="#hero">Home</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#about">About</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#timeline">Timeline</a>
            </li>

            <a class="navbar-brand d-none d-lg-block" href="#hero">
              THAN's Medic Care
              <strong class="d-block">Health Specialist</strong>
            </a>

            <li class="nav-item">
              <a class="nav-link" href="#reviews">Testimonials</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#booking">Booking</a>
            </li>
            <li class="nav-item">
                <!-- Link to Admin Page -->
                <router-link class="nav-link text-danger" to="/admin">Admin</router-link>
            </li>
          </template>

          <!-- ADMIN PAGE LINKS (Only show if on Admin) -->
          <template v-else>
            <li class="nav-item">
                <router-link class="nav-link" to="/">Back to Home</router-link>
            </li>
             <router-link class="navbar-brand d-none d-lg-block mx-auto" to="/">
              THAN's Medic Care
              <strong class="d-block">Admin Panel</strong>
            </router-link>
          </template>

        </ul>
      </div>
    </div>
  </nav>
</template>

<script setup>
import { useRoute } from 'vue-router';
const route = useRoute();
</script>