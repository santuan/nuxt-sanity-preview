<template>
  <div>
    <div class="flex flex-col PlugBlockeditorGrillaDoble md:flex-row">
      <div class="flex flex-col items-start justify-center w-full bg-gray-100">
        <h2 class="p-3 text-4xl font-bold md:px-12 md:py-0">
          {{ props?.heading }}
        </h2>
        <!-- <div class="prose">
          <SanityContent :blocks="props?.body" />
        </div> -->
      </div>
      <!-- <div class="relative w-full overflow-hidden">
        <PortableTextGalleryFour :imagesGallery="props?.imagesGallery"/>
      </div> -->
    </div>
  </div>
</template>

<script setup>
const props = defineProps(["heading", "body", "imagesGallery"]);
</script>
