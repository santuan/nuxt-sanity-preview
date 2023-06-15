<template>
  <ClientOnly>
    <div class="grid grid-cols-2 bg-indigo-200">
      <a
        v-for="image in imagesGallery"
        class=""
        :href="$urlFor(image.asset).width(600).height(300).url()"
      >
        <SanityImage :asset-id="image.asset._ref" auto="format" />
      </a>
    </div>
  </ClientOnly>
</template>

<script setup lang="ts">
const props = defineProps(["imagesGallery"]);
</script>
