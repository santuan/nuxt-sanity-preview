<template>
  <div class="relative z-10 max-w-screen-sm">
    <p class="fVeafc in">
      Hi {{ user?.email }}
      <button @click="logout" class="ieMfVH" :disabled="loading">
        <span class="fKlELC" :class="{ loading: loading }"> Log out </span>
        <svg
          viewBox="0 0 16 16"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
          class="jjoFVh"
          :class="{ loading: loading }"
        >
          <g
            fill="none"
            stroke-width="1.5"
            stroke-linecap="round"
            class="faEWLr"
            style="stroke: var(--icon-color)"
          >
            <circle stroke-opacity=".2" cx="8" cy="8" r="6"></circle>
            <circle cx="8" cy="8" r="6" class="VFMrX"></circle>
          </g>
        </svg>
      </button>
    </p>
    <h1 class="kKxhrq">Cantera Preview</h1>
    <div class="uQxNj">
      <NuxtLink class="ieMfVH" to="/app/nuestra-historia">
        <span class="fKlELC"> Nuestra historia </span>
      </NuxtLink>
      <NuxtLink class="ieMfVH" to="/app/quienes-somos">
        <span class="fKlELC"> Quienes somos </span>
      </NuxtLink>
    </div>
    <div class="uQxNj">
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
