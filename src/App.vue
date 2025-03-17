<script setup>
import { ref } from 'vue'
import VueScrollTo from 'vue-scrollto'
import 'vue3-carousel/dist/carousel.css'
import { Carousel, Slide, Navigation } from 'vue3-carousel'

const carouselImages = [
  'https://cdn.milenio.com/uploads/media/2023/03/22/quinta-llama-salon-eventos-fiestas_0_1_1200_745.jpg',
  'https://i.pinimg.com/736x/ee/7e/cd/ee7ecd6e9c0186de8c0d9208210e77f1.jpg',
  '/src/assets/images/quinta3.jpg',
  '/src/assets/images/quinta4.jpg'
]

const services = [
  {
    title: 'Alquiler del Salón',
    description: 'Amplio espacio con capacidad para 200 personas, totalmente climatizado y con iluminación moderna.',
    icon: 'fas fa-building'
  },
  {
    title: 'Área de Alberca',
    description: 'Piscina con área de descanso, sombrillas y tumbonas para disfrutar al aire libre.',
    icon: 'fas fa-swimming-pool'
  },
  {
    title: 'Cocina Equipada',
    description: 'Cocina industrial completamente equipada con electrodomésticos modernos.',
    icon: 'fas fa-utensils'
  },
  {
    title: 'Estacionamiento',
    description: 'Amplio estacionamiento privado con capacidad para 50 vehículos.',
    icon: 'fas fa-car'
  },
  {
    title: 'Área Techada',
    description: 'Espacio versátil techado ideal para eventos al aire libre.',
    icon: 'fas fa-umbrella'
  },
  {
    title: 'Opcionales',
    description: 'Servicios adicionales como DJ, decoración, catering y más.',
    icon: 'fas fa-plus-circle'
  }
]

const events = [
  { name: 'Bodas', icon: 'fas fa-rings-wedding' },
  { name: 'Cumpleaños', icon: 'fas fa-birthday-cake' },
  { name: 'Baby Shower', icon: 'fas fa-baby-carriage' },
  { name: 'Eventos Corporativos', icon: 'fas fa-briefcase' }
]

const scrollToSection = (elementId) => {
  VueScrollTo.scrollTo(elementId, 1000, {
    easing: 'ease-in-out'
  })
}
</script>

<template>
  <nav class="navbar animate__animated animate__fadeInDown">
    <div class="nav-content">
      <div class="logo-carousel">
        <Carousel :autoplay="3000" :wrap-around="true">
          <Slide v-for="(image, index) in carouselImages" :key="index">
            <div class="carousel-item">
              <img :src="image" alt="Quinta Los Nogales" />
            </div>
          </Slide>
          <template #addons>
            <Navigation />
          </template>
        </Carousel>
      </div>
      <div class="nav-links">
        <a class="nav-link animate__animated animate__fadeIn" @click="scrollToSection('#inicio')">Inicio</a>
        <a class="nav-link animate__animated animate__fadeIn" @click="scrollToSection('#servicios')">Servicios</a>
        <a class="nav-link animate__animated animate__fadeIn" @click="scrollToSection('#eventos')">Eventos</a>
        <a class="nav-link animate__animated animate__fadeIn" @click="scrollToSection('#reservacion')">Reservación</a>
      </div>
      <button class="reserve-button animate__animated animate__pulse animate__infinite" @click="scrollToSection('#reservacion')">
        Reservar Ahora
      </button>
    </div>
  </nav>

  <section id="inicio" class="hero">
    <div class="hero-content animate__animated animate__fadeIn">
      <h1 class="animate__animated animate__slideInDown">Quinta Los Nogales</h1>
      <p class="animate__animated animate__slideInUp">El lugar ideal para tus eventos y reuniones</p>
      <button class="reserve-button animate__animated animate__pulse animate__infinite" @click="scrollToSection('#reservacion')">
        Reservar Ahora
      </button>
    </div>
  </section>

  <section id="servicios" class="services">
    <h2 class="animate__animated animate__fadeIn">Servicios</h2>
    <div class="services-grid">
      <div v-for="(service, index) in services" 
           :key="index" 
           class="service-card animate__animated animate__fadeInUp"
           :style="{ 'animation-delay': `${index * 0.2}s` }">
        <i :class="service.icon" class="service-icon"></i>
        <h3>{{ service.title }}</h3>
        <p>{{ service.description }}</p>
      </div>
    </div>
  </section>

  <section id="eventos" class="events">
    <h2 class="animate__animated animate__fadeIn">Eventos</h2>
    <div class="events-content animate__animated animate__slideInUp">
      <h3>Tipos de Eventos</h3>
      <ul>
        <li v-for="(event, index) in events" 
            :key="index"
            class="animate__animated animate__fadeInLeft"
            :style="{ 'animation-delay': `${index * 0.2}s` }">
          <i :class="event.icon"></i>
          {{ event.name }}
        </li>
      </ul>
    </div>
  </section>

  <section id="reservacion" class="reservation">
    <h2 class="animate__animated animate__fadeIn">Reservación</h2>
    <div class="reservation-form animate__animated animate__zoomIn">
      <h3>¡Haz tu reservación ahora!</h3>
      <p>Formulario de reservación próximamente...</p>
    </div>
  </section>

  <footer id="ubicacion">
    <div class="footer-content">
      <div class="location animate__animated animate__fadeInUp">
        <h3>Ubicación</h3>
        <p><i class="fas fa-map-marker-alt"></i> 27268 Rancho de los Nogales, 27268 Torreón, Coah.</p>
      </div>
      <div class="social animate__animated animate__fadeInUp" style="animation-delay: 0.2s">
        <h3>Síguenos</h3>
        <div class="social-links">
          <a href="#" class="social-link"><i class="fab fa-instagram"></i></a>
          <a href="#" class="social-link"><i class="fab fa-facebook"></i></a>
          <a href="#" class="social-link"><i class="fab fa-whatsapp"></i></a>
        </div>
      </div>
    </div>
  </footer>
</template>

<style scoped>
.service-icon {
  font-size: 2.5rem;
  color: #ffd700;
  margin-bottom: 1rem;
}

.service-card h3 {
  margin: 1rem 0;
}

.service-card p {
  color: #666;
  line-height: 1.6;
}

.events-content li i {
  margin-right: 1rem;
  color: #ffd700;
}

.location i {
  margin-right: 0.5rem;
  color: #ffd700;
}

.social-link i {
  font-size: 1.5rem;
}
</style>