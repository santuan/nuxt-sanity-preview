<template>
  <div>
    <header
      v-if="user"
      class="flex items-center justify-between w-full p-3 border-b border-gray-300 shadow"
    >
      <div class="w-44">
        <NuxtLink to="/" class="btn gap-2 !text-sm">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="24"
            height="24"
            viewBox="0 0 24 24"
          >
            <path
              fill="currentColor"
              d="m12 5.69l5 4.5V18h-2v-6H9v6H7v-7.81l5-4.5M12 3L2 12h3v8h6v-6h2v6h6v-8h3L12 3z"
            />
          </svg>
          Home
        </NuxtLink>
      </div>
      <div class="flex items-center gap-3">
        <p class="">{{ user?.email }}</p>
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
      </div>
    </header>
    <div class="min-h-screen">
      <slot />
    </div>
  </div>
</template>

<script setup lang="ts">
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
  setTimeout(() => {
    loading.value = false;
  }, 5000);
};

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
