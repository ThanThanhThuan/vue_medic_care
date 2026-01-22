<template>
  <section class="section-padding" id="admin">
    <div class="container">
      <div class="row">
        <div class="col-12">
          <h2 class="text-center mb-4">Admin Dashboard</h2>
          
          <div v-if="loading" class="text-center">Loading appointments...</div>
          
          <div v-else-if="error" class="alert alert-danger">{{ error }}</div>

          <div v-else class="table-responsive">
            <table class="table table-bordered table-hover shadow-sm">
              <thead class="table-light">
                <tr>
                  <th>ID</th>
                  <th>Name</th>
                  <th>Email</th>
                  <th>Phone</th>
                  <th>Appt Date</th>
                  <th>Message</th>
                  <th>Submitted On</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="booking in bookings" :key="booking.id">
                  <td>{{ booking.id }}</td>
                  <td><strong>{{ booking.name }}</strong></td>
                  <td><a :href="'mailto:' + booking.email">{{ booking.email }}</a></td>
                  <td>{{ booking.phone }}</td>
                  <td>{{ formatDate(booking.booking_date) }}</td>
                  <td>{{ booking.message }}</td>
                  <td class="text-muted small">{{ formatDateTime(booking.created_at) }}</td>
                </tr>
                <tr v-if="bookings.length === 0">
                  <td colspan="7" class="text-center">No appointments found.</td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue';

const bookings = ref([]);
const loading = ref(true);
const error = ref(null);

// Fetch data when component mounts
onMounted(async () => {
  try {
    // const response = await fetch('http://localhost:3000/api/bookings');
    const response = await fetch(`${import.meta.env.VITE_API_BASE_URL}/bookings`);
    if (!response.ok) throw new Error('Failed to fetch data');
    bookings.value = await response.json();
  } catch (err) {
    error.value = err.message;
  } finally {
    loading.value = false;
  }
});

// Helper to format Date (YYYY-MM-DD)
const formatDate = (dateString) => {
  if (!dateString) return '-';
  return new Date(dateString).toLocaleDateString();
};

// Helper to format Timestamp
const formatDateTime = (dateString) => {
  if (!dateString) return '-';
  return new Date(dateString).toLocaleString();
};
</script>

<style scoped>
/* Add a little top margin so it doesn't hide behind fixed navbar */
#admin {
  margin-top: 80px; 
}
</style>