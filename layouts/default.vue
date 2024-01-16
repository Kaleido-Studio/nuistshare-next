<script setup lang="ts">

</script>

<template>
  <nav
      class="w-[100%] fixed top-0 left-0 z-50 backdrop-blur border-b-2 dark:border-b-gray-800 border-b-gray-100">
    <div class="flex h-[60px] items-center flex-row pl-4 pr-4">
      <h1 class="text-2xl font-bold">Nuistshare</h1>
      <span class="flex-grow"/>
      <UAvatar icon="i-mdi-account"/>
    </div>
  </nav>
  <div class="mt-[90px] flex sm:ml-40 sm:mr-40 max-sm:mr-8 max-sm:ml-8">
    <slot/>
  </div>
</template>

<style scoped lang="postcss">

</style>