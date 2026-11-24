
<script setup lang="ts">
import { ref } from 'vue'

const activeMenu = ref('Workspace')
const searchQuery = ref('')

const menus = ['Workspace', 'Collections', 'Environments', 'History']
</script>

<template>
  <header class="h-16 w-full bg-white border-b border-gray-200 flex items-center justify-between px-6">
    <!-- Left: Logo and navigation -->
    <div class="flex items-center gap-10">
      <!-- Logo -->
      <div class="flex items-center gap-2">
        <div class="w-9 h-9 rounded-lg bg-violet-600 flex items-center justify-center">
          <svg
            class="w-5 h-5 text-white"
            fill="none"
            stroke="currentColor"
            viewBox="0 0 24 24"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M8 5l-5 7 5 7M16 5l5 7-5 7M14 4l-4 16"
            />
          </svg>
        </div>

        <span class="text-xl font-bold tracking-tight text-gray-900">
          API<span class="text-violet-600">Forge</span>
        </span>
      </div>

      <!-- Navigation -->
      <nav class="hidden md:flex items-center gap-1">
        <button
          v-for="menu in menus"
          :key="menu"
          @click="activeMenu = menu"
          :class="[
            'px-4 py-2 rounded-lg text-sm font-medium transition-colors',
            activeMenu === menu
              ? 'bg-violet-50 text-violet-700'
              : 'text-gray-500 hover:bg-gray-100 hover:text-gray-900'
          ]"
        >
          {{ menu }}
        </button>
      </nav>
    </div>

    <!-- Right: Search and account -->
    <div class="flex items-center gap-4">
      <!-- Search -->
      <div class="hidden lg:flex items-center relative">
        <svg
          class="w-4 h-4 text-gray-400 absolute left-3"
          fill="none"
          stroke="currentColor"
          viewBox="0 0 24 24"
        >
          <circle cx="11" cy="11" r="7" stroke-width="2" />
          <path d="m16 16 4 4" stroke-width="2" stroke-linecap="round" />
        </svg>

        <input
          v-model="searchQuery"
          type="text"
          placeholder="Search anything..."
          class="w-56 pl-9 pr-3 py-2 bg-gray-50 border border-gray-200 rounded-lg text-sm outline-none focus:border-violet-400 focus:ring-2 focus:ring-violet-100"
        />

        <span class="absolute right-3 text-xs text-gray-400">⌘ K</span>
      </div>

      <!-- Help -->
      <button
        class="w-9 h-9 flex items-center justify-center rounded-lg text-gray-500 hover:bg-gray-100"
        title="Help"
      >
        <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <circle cx="12" cy="12" r="9" stroke-width="1.8" />
          <path
            stroke-linecap="round"
            stroke-width="1.8"
            d="M9.6 9a2.4 2.4 0 1 1 4.1 1.7c-.9.8-1.7 1.1-1.7 2.3M12 16.5h.01"
          />
        </svg>
      </button>

      <!-- Notifications -->
      <button
        class="relative w-9 h-9 flex items-center justify-center rounded-lg text-gray-500 hover:bg-gray-100"
        title="Notifications"
      >
        <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="1.8"
            d="M18 9a6 6 0 0 0-12 0c0 7-3 7-3 9h18c0-2-3-2-3-9M10 21h4"
          />
        </svg>
        <span class="absolute top-1.5 right-1.5 w-2 h-2 bg-red-500 rounded-full"></span>
      </button>

      <div class="h-8 w-px bg-gray-200"></div>

      <!-- User profile -->
      <button class="flex items-center gap-2 hover:bg-gray-50 rounded-lg p-1.5">
        <div class="w-8 h-8 rounded-full bg-violet-100 text-violet-700 flex items-center justify-center text-sm font-semibold">
          JD
        </div>

        <div class="hidden sm:block text-left">
          <p class="text-sm font-semibold text-gray-800">John Doe</p>
          <p class="text-xs text-gray-400">Administrator</p>
        </div>

        <svg class="w-4 h-4 text-gray-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="m7 10 5 5 5-5" />
        </svg>
      </button>
    </div>
  </header>
</template>