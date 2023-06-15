<template>
  <div class="w-full bg-gray-100">
    <div
      class="w-full max-w-full py-24 mx-auto prose text-white bg-gradient-to-br from-pink-600 to-indigo-600"
    >
      <div class="max-w-2xl mx-auto">
        <h1 class="text-white">{{ pageData?.data?.value?.title }}</h1>
        <pre>Slug: {{ $route.params.slug[0] }}</pre>
        <p>{{ pageData?.data?.value?.description }}</p>
      </div>
    </div>
    <SanityContent
      :blocks="pageData?.data?.value?.content"
      :serializers="serializers"
    />
  </div>
</template>

<script setup>
definePageMeta({
  layout: "app",
});

import { ref } from "vue";
const route = useRoute();
const slug = ref(route.params.slug[0]);
const url = slug.value;
const query = groq`*[_type == "page"&& slug.current == $url][0]`;
const pageData = useSanityQuery(query, { url });

import PlugBlockeditorGrillaDoble from "~/components/PortableText/PlugBlockeditorGrillaDoble.vue";
import PlugBlockeditor from "~/components/PortableText/PlugBlockeditor.vue";
import PlugBlockeditorHero from "~/components/PortableText/PlugBlockeditorHero.vue";
import BlockGallery from "~/components/PortableText/BlockGallery.vue";

const serializers = {
  types: {
    PlugBlockeditorGrillaDoble,
    PlugBlockeditor,
    PlugBlockeditorHero,
    BlockGallery,
  },
  marks: {
    // You can also just pass a string for a custom serializer if it's an HTML element
    internalLink: "a",
  },
};
</script>
