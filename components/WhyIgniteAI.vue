<template>
  <section class="value-proposition py-16 md:py-20" ref="valueProposition">
    <div class="container mx-auto px-6">
      <div
        class="flex flex-col md:flex-row items-center justify-between text-center md:text-left"
      >
        <!-- Logo di Sebelah Kiri -->
        <div
          class="md:w-1/3 flex justify-center md:justify-start opacity-0"
          ref="logo"
        >
          <img
            src="~/assets/images/Slide-2-Coin.png"
            alt="IgniteAI Logo"
            class="w-48 md:w-80"
          />
        </div>
        <!-- Teks di Sebelah Kanan -->
        <div
          class="md:w-2/3 mt-8 md:mt-0 opacity-0 translate-y-10"
          ref="content"
        >
          <h1
            class="text-3xl md:text-6xl lg:text-8xl font-extrabold mb-6 md:mb-8 text-white"
          >
            Why IgniteAI is the Future of AI Agents
          </h1>
          <p class="text-lg md:text-2xl font-semibold mb-6 md:mb-8 text-white">
            In a world overwhelmed by tools that can’t keep up, IgniteAI’s
            Intelligent AI Agents redefine what’s possible. These AI companions
            adapt to your needs, solve real-world challenges, and empower you to
            stay ahead—whether in finance, health, business, or creativity.
          </p>
          <!-- List Items -->
          <div
            class="bg-black border border-white border-3 rounded-lg shadow-lg p-6 md:p-4 flex flex-col md:flex-row md:space-x-6 lg:space-x-12 transition-all hover:shadow-xl opacity-0 translate-y-10"
            ref="listItems"
          >
            <div
              class="flex flex-col space-y-4 md:flex-row md:space-y-0 md:space-x-6 w-full text-left"
            >
              <!-- List Item 1 -->
              <div class="flex items-center space-x-2">
                <div class="w-3 h-3 bg-white rounded-full"></div>
                <h3 class="text-sm md:text-base font-semibold text-white">
                  AI that learns and evolves with you.
                </h3>
              </div>
              <!-- List Item 2 -->
              <div class="flex items-center space-x-2">
                <div class="w-3 h-3 bg-white rounded-full"></div>
                <h3 class="text-sm md:text-base font-semibold text-white">
                  Practical, affordable, and scalable.
                </h3>
              </div>
              <!-- List Item 3 -->
              <div class="flex items-center space-x-2">
                <div class="w-3 h-3 bg-white rounded-full"></div>
                <h3 class="text-sm md:text-base font-semibold text-white">
                  Designed to simplify complexity and amplify results.
                </h3>
              </div>
            </div>
          </div>
          <!-- Tombol -->
          <div
            class="flex justify-center mt-6 opacity-0 translate-y-10"
            ref="button"
          >
            <button class="cosmic-button cosmic-button-white">
              Explore the Technology
            </button>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

// Initialize GSAP plugins
gsap.registerPlugin(ScrollTrigger)

const valueProposition = ref(null)
const logo = ref(null)
const content = ref(null)
const listItems = ref(null)
const button = ref(null)

onMounted(() => {
  // Parallax effect for logo
  gsap.to(logo.value, {
    scrollTrigger: {
      trigger: valueProposition.value,
      start: 'top bottom',
      end: 'bottom top',
      scrub: true,
    },
    opacity: 2,
    y: -50, // Adjust this value for parallax intensity
    ease: 'none',
  })

  // Animate Content (Header, Description, List Items, Button)
  gsap.set([content.value, listItems.value, button.value], {
    opacity: 0,
    y: 50,
  })

  gsap.to(content.value, {
    scrollTrigger: {
      trigger: content.value,
      start: 'top 80%',
      toggleActions: 'play none none reverse',
    },
    opacity: 1,
    y: 0,
    duration: 1,
    ease: 'power2.out',
  })

  gsap.to(listItems.value, {
    scrollTrigger: {
      trigger: listItems.value,
      start: 'top 80%',
      toggleActions: 'play none none reverse',
    },
    opacity: 1,
    y: 0,
    duration: 1,
    delay: 0.3, // Delay animation for staggered effect
    ease: 'power2.out',
  })

  gsap.to(button.value, {
    scrollTrigger: {
      trigger: button.value,
      start: 'top 80%',
      toggleActions: 'play none none reverse',
    },
    opacity: 1,
    y: 0,
    duration: 1,
    delay: 0.6, // Delay animation for staggered effect
    ease: 'power2.out',
  })
})
</script>

<style scoped>
.value-proposition {
  background-image: url('@/assets/images/Slide-2-BG.png');
  background-size: cover;
  background-position: center;
  min-height: 100vh;
  display: flex;
  align-items: center;
}
.cosmic-button {
  @apply border-2 px-6 md:px-8 py-3 rounded-full text-lg font-bold transition-all duration-300 shadow-[0_0_20px_rgba(255,255,255,0.3)];
}
.cosmic-button-white {
  @apply border-black text-black bg-white hover:bg-black hover:text-white;
}
@media (max-width: 768px) {
  .value-proposition {
    @apply text-center;
  }
  .value-proposition h1 {
    @apply text-3xl;
  }
  .value-proposition p {
    @apply text-lg;
  }
  /* Biar List Item lebih rapi di Mobile */
  .bg-black {
    @apply flex flex-col space-y-4 p-6 rounded-lg;
  }
}
</style>
