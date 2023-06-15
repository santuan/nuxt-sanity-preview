<template>
  <div  class="flex items-center justify-center w-full h-screen ">
      <div
        class="relative z-50 w-full mx-auto DaoRb max-w-75"
      >
        <h1 class="eSHwvX">Sign in</h1>
        <form @submit.prevent="login">
          <ErrorAlert :error-msg="authError" @clearError="clearError" />
          <div class="jGQTZC">
            <label class="iJLvzO">
              <div class="fdCSlG">
                <input
                  class="cmCuLh"
                  type="text"
                  placeholder="Email address"
                  v-model="email"
                />
              </div>
            </label>
            <label class="iJLvzO">
              <div class="fdCSlG">
                <input
                  class="cmCuLh"
                  type="password"
                  placeholder="Password"
                  v-model="password"
                />
              </div>
            </label>
          </div>
          <div class="jGQTZC">
            <button class="gZMQdu" type="submit" :disabled="loading">
              <div class="bjhGPG" :class="{ loading: loading }">Sign in</div>
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
        </form>
      </div>
    </div>
</template>


<script setup>
useHead({
  title: "Login | supaAuth",
});

const user = useSupabaseUser();
const loading = ref(false);
const authError = ref("");
const email = ref("");
const password = ref("");
const client = useSupabaseAuthClient();

const login = async () => {
  loading.value = true;
  const { error } = await client.auth.signInWithPassword({
    email: email.value,
    password: password.value,
  });
  if (error) {
    loading.value = false;
    authError.value = "Invalid login credentials";
    setTimeout(() => {
      authError.value = "";
    }, 5000);
  }
};

const clearError = () => {
  authError.value = "";
};
</script>