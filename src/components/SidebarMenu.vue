<script setup>
import { ref, watch } from 'vue'
import { RouterLink } from 'vue-router'

const isExpanded = ref(true)
const emit = defineEmits(['toggle'])

const toggleSidebar = () => {
  isExpanded.value = !isExpanded.value
  emit('toggle', isExpanded.value)
}

// Watch for changes to emit initially when component mounts
watch(
  isExpanded,
  (newValue) => {
    emit('toggle', newValue)
  },
  { immediate: true },
)

// Menu items array - you can customize this based on your needs
const menuItems = [
  { name: 'Dashboard', path: '/', icon: '📊' },
  { name: 'Products', path: '/products', icon: '📦' },
  { name: 'Orders', path: '/orders', icon: '🛒' },
  { name: 'Customers', path: '/customers', icon: '👥' },
  { name: 'Reports', path: '/reports', icon: '📈' },
  { name: 'Settings', path: '/settings', icon: '⚙️' },
]
</script>

<template>
  <div class="sidebar-container">
    <div class="sidebar" :class="{ 'sidebar-collapsed': !isExpanded }">
      <div class="sidebar-header">
        <div class="logo-container">
          <img v-if="isExpanded" src="@/assets/logo.svg" alt="Logo" class="logo" />
          <img v-else src="@/assets/logo.svg" alt="Logo" class="logo-small" />
        </div>
        <button class="toggle-btn" @click="toggleSidebar">
          {{ isExpanded ? '◀' : '▶' }}
        </button>
      </div>

      <div class="sidebar-content">
        <nav class="nav-menu">
          <RouterLink
            v-for="item in menuItems"
            :key="item.path"
            :to="item.path"
            class="nav-item"
            active-class="active"
          >
            <span class="nav-icon">{{ item.icon }}</span>
            <span v-if="isExpanded" class="nav-text">{{ item.name }}</span>
          </RouterLink>
        </nav>
      </div>
    </div>
  </div>
</template>

<style scoped>
.sidebar-container {
  height: 100%;
  position: relative;
}

.sidebar {
  background-color: #2c3e50;
  color: white;
  height: 100vh;
  transition: width 0.3s ease;
  width: 250px;
  position: fixed;
  top: 0;
  left: 0;
  z-index: 100;
  display: flex;
  flex-direction: column;
}

.sidebar-collapsed {
  width: 60px;
}

.sidebar-header {
  padding: 1rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
}

.logo-container {
  display: flex;
  align-items: center;
  justify-content: center;
}

.logo {
  height: 40px;
  width: auto;
}

.logo-small {
  height: 30px;
  width: auto;
}

.toggle-btn {
  background: none;
  border: none;
  color: white;
  cursor: pointer;
  font-size: 1rem;
  padding: 0.25rem;
}

.sidebar-content {
  flex: 1;
  overflow-y: auto;
  padding-top: 1rem;
}

.nav-menu {
  display: flex;
  flex-direction: column;
}

.nav-item {
  display: flex;
  align-items: center;
  padding: 0.75rem 1rem;
  color: rgba(255, 255, 255, 0.8);
  text-decoration: none;
  transition: background-color 0.2s;
}

.nav-item:hover {
  background-color: rgba(255, 255, 255, 0.1);
  color: white;
}

.nav-item.active {
  background-color: #41b883;
  color: white;
}

.nav-icon {
  margin-right: 0.75rem;
  font-size: 1.2rem;
  min-width: 24px;
  text-align: center;
}

.nav-text {
  font-size: 0.9rem;
}
</style>
