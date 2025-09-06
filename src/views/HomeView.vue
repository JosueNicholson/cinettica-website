<script setup lang="ts">
import type HomeNavbar from '@/components/HomeNavbar.vue'
import ShowCard from '@/components/ShowCard.vue'

import SpotifyLogo from '@/components/icons/SpotifyLogo.vue'
import type { Show } from '@/types/show'
import { format } from 'date-fns'

const showsList: Array<Show> = [
  {
    cityName: 'CDB',
    stateName: 'Piauí',
    eventName: 'Carnaval Metal',
    date: format(new Date('2025-03-04T15:00:00.000Z'), 'dd LLL yyyy'),
    id: 1,
  },
  {
    cityName: 'Floriano',
    stateName: 'Piauí',
    eventName: 'Rock Festival',
    date: format(new Date('2025-03-04T15:00:00.000Z'), 'dd LLL yyyy'),
    id: 2,
  },
  {
    cityName: 'Teresina',
    stateName: 'Piauí',
    eventName: 'Piauí POP',
    date: format(new Date('2025-03-04T15:00:00.000Z'), 'dd LLL yyyy'),
    id: 3,
  },
  {
    cityName: 'São João',
    stateName: 'Piauí',
    eventName: 'Rebel Sound Festival',
    date: format(new Date('2025-03-04T15:00:00.000Z'), 'dd LLL yyyy'),
    id: 4,
  },
]

const singlesList = [
  {
    spotifyLink:
      'https://open.spotify.com/intl-pt/track/7mDoXHLNpLXy6WpWyiEtJ7?si=9de02cc5edd54f25',
    imageSource: '../../public/singles/silent-battle-wage.png',
    id: 1,
  },
  {
    spotifyLink:
      'https://open.spotify.com/intl-pt/track/65odKvNFX4Ml4j4r8BxTHj?si=adda9885b92a46b5',
    imageSource: '../../public/singles/lembrancas.png',
    id: 2,
  },
  {
    spotifyLink:
      'https://open.spotify.com/intl-pt/track/3zxoag6lG4Empr5eZtJI1m?si=b52b3ac423ce4e7c',
    imageSource: '../../public/singles/a-despedida.png',
    id: 3,
  },
  {
    spotifyLink:
      'https://open.spotify.com/intl-pt/track/2OIYwlkyd9E2vH0R2m6cCa?si=ab97b962ac7a4e14',
    imageSource: '../../public/singles/nada-pode-nos-parar.png',
    id: 4,
  },
]

const clipsList = [
  {
    src: 'uXIeRj4Rjzo',
    id: 1,
  },
  {
    src: 'WfhuFBrEF4c',
    id: 2,
  },
  {
    src: 'M6P4RtRMvkU',
    id: 3,
  },
  {
    src: 'ol-DzAqO28o',
    id: 4,
  },
]
// const newsList = []
</script>

<template>
  <div class="landing-page p-3">
    <HomeNavbar />

    <div class="flex flex-col items-center">
      <img src="../assets/cinettica-band-name-logo.png" alt="band-logo" />

      <p class="text-lg">
        Ouça agora o nosso novo single “Silent Battles Wage”, disponíveis em todas as plataformas
        digitais
      </p>

      <Button class="bg-main-gradient py-3 px-4 rounded mt-5 flex">
        <SpotifyLogo />
        <p class="ml-3 text-lg">Ouvir agora</p>
      </Button>
    </div>
  </div>

  <section class="p-3 -mt-[9px] bg-dark">
    <h3 class="text-5xl">Shows</h3>
    <div class="flex overflow-auto gap-6 mt-4">
      <ShowCard v-for="show in showsList" :key="show.id" :show-data="show" />
    </div>
  </section>

  <video
    autoplay
    loop
    muted
    playsinline
    preload="auto"
    class="w-full h-auto object-cover my-32 md:h-screen"
  >
    <source src="../assets/video-cinettica.mp4" type="video/mp4" />
  </video>

  <section class="p-3">
    <h3 class="text-5xl">Singles</h3>
    <div class="flex overflow-auto gap-6 mt-4">
      <SingleCard v-for="single in singlesList" :key="single.id" :data="single" />
    </div>
  </section>

  <section class="p-3">
    <h3 class="text-5xl">Nossos vídeos</h3>
    <div class="flex overflow-auto gap-6 mt-4">
      <iframe
        v-for="videoClip in clipsList"
        :key="videoClip.id"
        width="320"
        height="240"
        :src="`https://www.youtube.com/embed/${videoClip.src}`"
        title="YouTube video player"
        frameborder="0"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
        allowfullscreen
      >
      </iframe>
    </div>
  </section>

  <section class="p-3">
    <h3 class="text-5xl">Notícias</h3>
    <div class="flex overflow-auto gap-6">
      <!-- <NewsCard v-for="news in newsList" :key="news.id" :data="news" /> -->
    </div>
  </section>

  <section class="footer flex flex-col text-montserrat">
    <div class="flex flex-col items-center justify-center grow-1">
      <p class="text-3xl text-center font-bold md:w-1/2">
        Cadastre-se no nosso site e seja o primeiro a ficar por dentro das novidades
      </p>

      <Button class="bg-transparent py-3 px-4 rounded mt-5 w-1/2 border-2 md:w-1/4"
        >Cadastre-se</Button
      >
      <Button class="bg-main-gradient py-3 px-4 rounded mt-5 w-1/2 md:w-1/4">Entrar</Button>
    </div>

    <div class="flex gap-4 justify-center mb-4">
      <a href=""><span class="pi pi-facebook text-2xl"></span></a>
      <a href=""><span class="pi pi-instagram text-2xl"></span></a>
      <a href=""><span class="pi pi-youtube text-2xl"></span></a>
      <a href=""><span class="pi pi-twitter text-2xl"></span></a>
    </div>
    <div class="flex flex-col items-center text-sm">
      <span>2025 Cinéttica.</span>
      <span>Todos os direitos reservados</span>
    </div>
  </section>
</template>

<style scoped lang="scss">
.landing-page {
  min-height: 100vh;

  &::before {
    content: '';
    position: absolute;
    inset: 0;
    background: url('../assets/landing-image.png') 50% / cover no-repeat;
    opacity: 0.5;
    z-index: -1;
  }
}

.footer {
  min-height: 100vh;
  position: relative;

  &::before {
    content: '';
    position: absolute;
    inset: 0;
    background: url('../assets/cinettica-footer-picture.jpg') 50% / cover no-repeat;
    opacity: 0.5;
    z-index: -1;
  }
}
</style>
