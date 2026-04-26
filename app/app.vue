<template>
  <div id="app-root">
    <NuxtLayout>
      <NuxtPage />
    </NuxtLayout>
    <UToaster />
  </div>
</template>

<style>
/* Reset global shadows that might be coming from themes or frameworks */
html, body, #__nuxt {
  box-shadow: none !important;
}

/* Re-allow shadows only for our specific premium classes if needed, 
   but for now let's be aggressive to find the source */

.page-enter-active,
.page-leave-active {
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}
.page-enter-from,
.page-leave-to {
  opacity: 0;
  transform: translateY(10px);
  filter: blur(10px);
}
</style>
