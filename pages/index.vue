<!-- pages/index.vue -->
<template>
  <div class="min-h-screen bg-black flex flex-col items-center justify-center">
    <div class="relative z-10 text-center">
      <h1 class="text-4xl md:text-6xl font-bold text-white mb-4">Próximamente</h1>
      <p class="text-lg md:text-xl text-gray-300 mb-8">Nuestro sitio web se lanzará en:</p>
      <div class="flex justify-center space-x-4 mb-8">
        <div class="bg-white bg-opacity-10 p-4 rounded-lg">
          <span class="text-4xl md:text-5xl font-bold text-white">{{ days }}</span>
          <span class="text-lg md:text-xl text-gray-300 block">Días</span>
        </div>
        <div class="bg-white bg-opacity-10 p-4 rounded-lg">
          <span class="text-4xl md:text-5xl font-bold text-white">{{ hours }}</span>
          <span class="text-lg md:text-xl text-gray-300 block">Horas</span>
        </div>
        <div class="bg-white bg-opacity-10 p-4 rounded-lg">
          <span class="text-4xl md:text-5xl font-bold text-white">{{ minutes }}</span>
          <span class="text-lg md:text-xl text-gray-300 block">Minutos</span>
        </div>
        <div class="bg-white bg-opacity-10 p-4 rounded-lg">
          <span class="text-4xl md:text-5xl font-bold text-white">{{ seconds }}</span>
          <span class="text-lg md:text-xl text-gray-300 block">Segundos</span>
        </div>
      </div>

    </div>
    <div class="absolute inset-0 z-0">
      <svg class="animate-pulse" viewBox="0 0 1920 1080" fill="none" xmlns="http://www.w3.org/2000/svg">
        <rect width="1920" height="1080" fill="url(#gradient)" />
        <defs>
          <radialGradient id="gradient" cx="0" cy="0" r="1" gradientUnits="userSpaceOnUse"
            gradientTransform="translate(960 540) rotate(90) scale(540 960)">
            <stop stop-color="#7F00FF" stop-opacity="0.8" />
            <stop offset="1" stop-color="#E100FF" stop-opacity="0.2" />
          </radialGradient>
        </defs>
      </svg>
    </div>
  </div>
</template>

<script setup>

useHead({
  title: 'Platform.cl - Desarrollamos aplicaciones web',
  meta: [
    {
      name: 'description',
      content: 'Platform.cl - Desarrollamos aplicaciones web. Nuestro sitio web se lanzará pronto. ¡Mantente atento!',
    },
  ],
  link: [
    {
      rel: 'icon',
      type: 'image/png',
      href: '/favicon-16x16.png',
      sizes: '16x16',
    },
    {
      rel: 'icon',
      type: 'image/png',
      href: '/favicon-32x32.png',
      sizes: '32x32',
    },
    {
      rel: 'apple-touch-icon',
      href: '/apple-touch-icon.png',
      sizes: '180x180',
    },
  ],
});

const launchDate = new Date('2024-05-21').getTime();

const days = ref(0);
const hours = ref(0);
const minutes = ref(0);
const seconds = ref(0);

let countdown;

onMounted(() => {
  countdown = setInterval(updateCountdown, 1000);
});

onUnmounted(() => {
  clearInterval(countdown);
});

function updateCountdown() {
  const now = new Date().getTime();
  const distance = launchDate - now;

  days.value = Math.floor(distance / (1000 * 60 * 60 * 24));
  hours.value = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
  minutes.value = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
  seconds.value = Math.floor((distance % (1000 * 60)) / 1000);
}
</script>