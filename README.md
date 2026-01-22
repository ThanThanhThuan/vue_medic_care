# Frontend (Vue 3 + Vite) for Medic Care App

I migrated a static Bootstrap 5 HTML template into a modern Vue 3 application, adding routing and dynamic API integration.
Credit for the template: https://templatemo.com/tm-566-medic-care
Watch live at : https://vue-medic-care.onrender.com/ 
Book an appointment, then click Admin to see results.
<img width="1243" height="878" alt="image" src="https://github.com/user-attachments/assets/8d6444b6-0232-4f9f-9e98-561aeac041f6" />

Tech Stack

    Framework: Vue 3 (Composition API with <script setup>)

    Build Tool: Vite

    Styling: Bootstrap 5 (Legacy CSS/JS loaded globally)

    Routing: Vue Router 4

Key Features

    Template Migration:

        Moved static assets (css, js, images, fonts) to the public/ folder so they are served at the root path.

        Sliced index.html into modular components: NavBar, HeroSection, AboutSection, TimelineSection, TestimonialsSection, BookingSection, and FooterSection.

    Navigation & Routing:

        Implemented Vue Router to create a Multi-Page Application feel.

        Views:

            HomeView.vue: The public landing page.

            AdminView.vue: A dashboard to view the list of appointments.

        Smart Navbar: Dynamically changes links based on the current route (e.g., shows "Back to Home" when on the Admin page).

    API Integration:

        Booking Form: Uses fetch (POST) to send user input to the backend. Includes loading states and success/error notifications.

        Admin Dashboard: Uses fetch (GET) inside onMounted to retrieve and display appointment data in a table.

        Environment Config: Used .env (VITE_API_BASE_URL) to manage the backend URL dynamically.

    Legacy Script Handling:

        Managed jQuery/Owl Carousel scripts by loading custom.js dynamically in onMounted to ensure the DOM is ready before legacy scripts run.

Project Structure
code Text

medic-care-vue/
├── public/              # Static assets (css, fonts, images, js)
├── src/
│   ├── components/      # UI Sections (BookingSection, NavBar, etc.)
│   ├── router/          # Router config (Home vs Admin)
│   ├── views/           # Page views (HomeView, AdminView)
│   ├── App.vue          # Root component
│   └── main.js          # App entry point
├── .env                 # VITE_API_BASE_URL config
└── index.html           # Entry HTML (loads CSS/Global JS)
