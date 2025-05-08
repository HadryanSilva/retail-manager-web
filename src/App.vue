<script setup>
import { ref } from 'vue'
import { RouterView } from 'vue-router'
import SidebarMenu from './components/SidebarMenu.vue'

const sidebarExpanded = ref(true)

const handleSidebarToggle = (isExpanded) => {
  sidebarExpanded.value = isExpanded
}
</script>

<template>
  <div class="app-container">
    <SidebarMenu @toggle="handleSidebarToggle" />
    <main class="main-content" :class="{ 'content-collapsed': !sidebarExpanded }">
      <RouterView />
    </main>
  </div>
</template>

<style>
/* Global styles are now moved to base.css and main.css */
.app-container {
  display: flex;
  height: 100vh;
}

.main-content {
  flex: 1;
  padding: 2rem;
  margin-left: var(--sidebar-width); /* Match the width of expanded sidebar */
  transition: margin-left 0.3s ease;
}

.content-collapsed {
  margin-left: var(--sidebar-collapsed-width); /* Match the width of collapsed sidebar */
}
</style>
