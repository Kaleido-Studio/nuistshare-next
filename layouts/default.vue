<script setup lang="ts">
import {Collapse} from 'vue-collapsed';

const openCollapsedMenu = ref(false)

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

const iconColorMode = computed(() => colorMode.value === 'dark' ? 'i-material-symbols-dark-mode' : 'i-material-symbols-light-mode')
const collapsedLinks = computed(() => [links, [{
  label: '切换颜色样式',
  icon: iconColorMode.value,
  click: toggleColorMode
}]])

function toggleColorMode() {
  colorMode.value === 'light' ? colorMode.preference = 'dark' : colorMode.preference = 'light'
}

const colorMode = useColorMode()
</script>

<template>
  <nav
      class="w-[100%] fixed top-0 left-0 max-sm:left-0 z-50 backdrop-blur-2xl border-b-2 dark:border-b-gray-800 border-b-gray-100">
    <div class="flex h-[60px] items-center flex-row pl-4 pr-4 space-x-2">
      <h1 class="text-2xl font-bold">Nuistshare</h1>
      <span class="flex-grow"/>
      <UAvatar icon="i-mdi-account" class="flex sm:hidden"/>
      <UButton icon="i-mdi-menu" variant="outline" class="sm:hidden" @click="openCollapsedMenu = !openCollapsedMenu"/>
      <UButton :icon="iconColorMode"
               @click="toggleColorMode"
               variant="ghost" color="gray" class="hidden sm:flex"/>
    </div>
    <ClientOnly>
      <Collapse :when="openCollapsedMenu" class="sm:hidden w-[100%] top-[60px]">
        <UVerticalNavigation :links="collapsedLinks" class="m-2"/>
      </Collapse>
    </ClientOnly>
  </nav>
  <nav
      class="hidden flex-col sm:flex w-60 h-[100%] fixed left-0 top-[60px] p-2 border-r-2 dark:border-r-gray-800 border-r-gray-100">
    <UButton to="/profile" class="w-[100%]" variant="ghost" size="lg" color="gray">
      <UAvatar icon="i-mdi-account"/>
      <span>未登录</span>
    </UButton>
    <span class="w-[100%] h-0.5 dark:bg-gray-800 bg-gray-100 mt-2 mb-2"/>
    <UVerticalNavigation :links="links"/>
  </nav>
  <div class="mt-[90px] flex sm:ml-80 sm:mr-20 max-sm:mr-8 max-sm:ml-8">
    <slot/>
  </div>
</template>

<style scoped lang="postcss">

</style>