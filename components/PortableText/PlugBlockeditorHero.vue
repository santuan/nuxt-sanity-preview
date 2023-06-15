<template>
  <div
    class="relative flex flex-col items-center justify-center pt-32 pb-32 overflow-hidden bg-red-600 PlugBlockeditorHero bg-gradient-to-tr from-red-400"
  >
    <h1
      class="relative z-10 font-sans text-4xl text-white md:text-6xl animate__fadeIn animate__animated"
    >
      {{ props?.heading }}
    </h1>
    <div class="relative z-10 prose prose-xl prose-invert">
      <SanityContent :blocks="props?.body" />
    </div>
  </div>
</template>

<script setup>
const props = defineProps(["heading", "body", "imagesGallery"]);
</script>
