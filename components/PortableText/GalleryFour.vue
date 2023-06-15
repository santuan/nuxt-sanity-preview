<template>
  <ClientOnly>
    <div class="grid grid-cols-2 bg-indigo-200">
      <a
        v-for="image in imagesGallery"
        class=""
        :href="$urlFor(image.asset).width(600).height(300).url()"
      >
        <img
          :src="$urlFor(image.asset).width(600).height(600).url()"
          class="object-cover w-full h-64 overflow-hidden !m-0"
        />
      </a>
    </div>
  </ClientOnly>
</template>

<script setup lang="ts">
const props = defineProps(["imagesGallery"]);
</script>
