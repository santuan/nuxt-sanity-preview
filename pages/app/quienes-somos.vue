<template>
  <div>
    <div class="py-24 text-center">
      <h1 class="text-2xl">{{ data?.title }}</h1>
    </div>
    <!-- <SanityContent :blocks="data?.content" :serializers="serializers" /> -->
  </div>
</template>

<script setup>
definePageMeta({
  layout: "app",
});
const query = groq`*[_type == "quienes_somos"]  | order(publishedAt desc) [0]`;
const { data } = useSanityQuery(query);

import PlugBlockeditorGrillaDoble from "~/components/PortableText/PlugBlockeditorGrillaDoble.vue";

const serializers = {
  types: {
    PlugBlockeditorGrillaDoble
  },
  marks: {
    // You can also just pass a string for a custom serializer if it's an HTML element
    internalLink: "a",
  },
};
</script>
