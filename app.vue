<script setup>
useHead({
  title: "corradUI - NuxtJS Admin Dashboard Template",
  description: "Home page",
  htmlAttrs: {
    lang: "en",
  },
  script: [
    {
      type: "module",
      innerHTML: `
        import Chatbot from "https://cdn.jsdelivr.net/npm/flowise-embed/dist/web.js"
        Chatbot.init({
          chatflowid: "3c484af8-2354-43a9-af68-ccb60b6ea3ec",
          apiHost: "https://chat.sena.my",
        })
      `
    }
  ]
});

const loading = ref(true);

onMounted(() => {
  // Hide loading indicator if not hydrating
  setTimeout(() => {
    loading.value = false;
  }, 1000);

  // Get theme from localStorage
  let theme = localStorage.getItem("theme") || "default";
  document.documentElement.setAttribute("data-theme", theme);
});
</script>

<template>
  <div>
    <NuxtLoadingIndicator />
    <NuxtLayout>
      <Loading v-if="loading" />
      <NuxtPage :key="$route.fullPath" v-else />
    </NuxtLayout>
  </div>
</template>
