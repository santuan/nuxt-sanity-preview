<template>
  <div class="max-w-4xl py-12 mx-auto prose prose-xl PlugBlockeditor">
    <SanityContent :blocks="props?.body" />
  </div>
</template>

<script setup>
const props = defineProps(["heading", "body"]);
console.log(props);
</script>
