<script lang="ts" setup>
interface Props {
  data: {
    imageSource: string
    spotifyLink: string
  }
}

defineProps<Props>()
</script>

<template>
  <a :href="data.spotifyLink" target="_blank" rel="noopener noreferrer">
    <Card>
      <template #header>
        <div class="relative">
          <img alt="single-img" :src="data.imageSource" />
          <div class="absolute group top-0 w-full h-full hover:bg-black/50">
            <SpotifyLogo
              class="absolute top-[calc(50%-15px)] right-[calc(50%-15px)] hidden group-hover:block"
            />
          </div>
        </div>
      </template>
    </Card>
  </a>
</template>
