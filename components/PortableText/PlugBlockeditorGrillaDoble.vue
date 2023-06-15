<template>
  <div>
    <div class="flex flex-col PlugBlockeditorGrillaDoble md:flex-row">
      <div class="flex flex-col items-start justify-center w-full p-3 bg-gray-100 md:px-12 md:py-0">
        <h2 class="text-4xl font-bold ">
          {{ props?.heading }}
        </h2>
        <div class="prose">
          <SanityContent :blocks="props?.body" />
        </div>
      </div>
      <div class="relative w-full overflow-hidden">
        <PortableTextGalleryFour :imagesGallery="props?.imagesGallery"/>
      </div>
    </div>
  </div>
</template>

<script setup>
const props = defineProps(["heading", "body", "imagesGallery"]);
</script>
