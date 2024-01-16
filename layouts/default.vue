<script setup lang="ts">
const links = [
  {
    label: '首页',
    icon: 'i-mdi-home',
    to: '/'
  },
  {
    label: '浏览',
    icon: 'i-mdi-compass',
    to: '/explore'
  }
]
</script>

<template>
  <nav
      class="w-[100%] fixed top-0 left-60 max-sm:left-0 z-50 backdrop-blur border-b-2 dark:border-b-gray-800 border-b-gray-100">
    <div class="flex h-[60px] items-center flex-row pl-4 pr-4">
      <h1 class="text-2xl font-bold">Nuistshare</h1>
      <span class="flex-grow"/>
      <UAvatar icon="i-mdi-account" class="flex sm:hidden"/>
    </div>
  </nav>
  <nav class="hidden flex-col sm:flex w-60 fixed left-0 top-0 p-2">
    <UButton class="w-[100%]" variant="ghost" size="lg" color="gray">
      <UAvatar icon="i-mdi-account"/>
      <span>未登录</span>
    </UButton>
    <span class="w-[100%] h-0.5 bg-gray-800"/>
    <UVerticalNavigation :links="links"/>
  </nav>
  <div class="mt-[90px] flex sm:ml-80 sm:mr-20 max-sm:mr-8 max-sm:ml-8">
    <slot/>
  </div>
</template>

<style scoped lang="postcss">

</style>