<template>
  <div class="relative z-10 max-w-6xl mx-auto mt-24">
    <p class="fVeafc in">
      Hola {{ user?.email }}
    </p>
    <h1 class="kKxhrq">Cantera Preview</h1>
    <div class="uQxNj">
      <NuxtLink class="ieMfVH" to="/app/nuestra-historia">
        <span class="fKlELC"> Nuestra historia </span>
      </NuxtLink>
      <NuxtLink class="ieMfVH" to="/app/quienes-somos">
        <span class="fKlELC"> Quienes somos </span>
      </NuxtLink>
      <NuxtLink
        v-for="item in data"
        :key="item.id"
        class="ieMfVH"
        :to="'app/' + item.slug.current"
      >
        <span class="fKlELC"> {{ item.title }} </span>
      </NuxtLink>
    </div>
  </div>
</template>

<script setup lang="ts">
definePageMeta({
  layout: "app",
});

const client = useSupabaseAuthClient();
const user = useSupabaseUser();
const loading = ref(false);

const logout = async () => {
  loading.value = true;
  const { error } = await client.auth.signOut();
  if (error) {
    loading.value = false;
    return alert("Something went wrong !");
  }
};

const query = groq`*[_type == "page"]  | order(publishedAt desc)`;

const { data } = useSanityQuery(query);

useHead({
  title: "supaAuth",
  meta: [
    {
      name: "description",
      content:
        "Authentication template with email and password, using Supabase. If you want to a quick start to your next Nuxt3 app, please feel free to use this template.",
    },
  ],
});
</script>
