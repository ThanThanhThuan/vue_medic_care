<template>
  <section class="section-padding" id="booking">
    <div class="container">
      <div class="row">
        <div class="col-lg-8 col-12 mx-auto">
          <div class="booking-form">
            <h2 class="text-center mb-lg-3 mb-2">Book an appointment</h2>
            
            <form role="form" @submit.prevent="submitForm">
              <div class="row">
                <div class="col-lg-6 col-12">
                  <input type="text" v-model="form.name" class="form-control" placeholder="Full name" required>
                </div>

                <div class="col-lg-6 col-12">
                  <input type="email" v-model="form.email" class="form-control" placeholder="Email address" required>
                </div>

                <div class="col-lg-6 col-12">
                  <input type="tel" v-model="form.phone" class="form-control" placeholder="Phone: 123-456-7890">
                </div>

                <div class="col-lg-6 col-12">
                  <input type="date" v-model="form.date" class="form-control">
                </div>

                <div class="col-12">
                  <textarea class="form-control" rows="5" v-model="form.message" placeholder="Additional Message"></textarea>
                </div>

                <div class="col-lg-3 col-md-4 col-6 mx-auto">
                  <button type="submit" class="form-control" id="submit-button" :disabled="loading">
                    {{ loading ? 'Sending...' : 'Book Now' }}
                  </button>
                </div>
              </div>
              
              <!-- Success/Error Messages -->
              <div v-if="statusMessage" :class="['alert mt-3', statusClass]" role="alert">
                {{ statusMessage }}
              </div>

            </form>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { reactive, ref } from 'vue';

const loading = ref(false);
const statusMessage = ref('');
const statusClass = ref('');

const form = reactive({
  name: '',
  email: '',
  phone: '',
  date: '',
  message: ''
});

const submitForm = async () => {
  loading.value = true;
  statusMessage.value = '';
  
  try {
    // const response = await fetch('http://localhost:3000/api/bookings', {
    const response = await fetch(`${import.meta.env.VITE_API_BASE_URL}/bookings`, {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json'
      },
      body: JSON.stringify(form)
    });

    const data = await response.json();

    if (response.ok) {
      statusClass.value = 'alert-success';
      statusMessage.value = 'Appointment booked successfully!';
      // Reset form
      Object.keys(form).forEach(key => form[key] = '');
    } else {
      throw new Error(data.error || 'Failed to book.');
    }

  } catch (error) {
    statusClass.value = 'alert-danger';
    statusMessage.value = error.message;
  } finally {
    loading.value = false;
  }
}
</script>