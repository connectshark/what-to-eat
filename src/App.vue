<script setup>
</script>

<template>
  <header class="sticky top-0 z-10 backdrop-blur-2xl border-b border-gray-200/50">
    <div class="w-11/12 container mx-auto flex items-center justify-between py-4">
      <router-link to="/" class="text-2xl font-bold text-gray-900">What To Eat</router-link>
      <nav class="space-x-2">
        <router-link to="/discover" class="hover:text-primary transition-colors">開始探索</router-link>
        <router-link to="/about" class="hover:text-primary transition-colors">關於我們</router-link>
      </nav>
    </div>
  </header>
  <main class="min-h-screen">
    <router-view />
  </main>
  <footer class="bg-gray-800 text-white py-10">
      <div class="container mx-auto px-4 text-center sm:flex sm:justify-between">
        <p class="mb-4 sm:mb-0">&copy; 2025 What To Eat. All Rights Reserved.</p>
        <nav>
          <router-link to="/about" class="px-3 py-2 hover:text-primary transition duration-300">關於我們</router-link>
          <router-link to="/contact" class="px-3 py-2 hover:text-primary transition duration-300">聯絡我們</router-link>
          <router-link to="/privacy" class="px-3 py-2 hover:text-primary transition duration-300">隱私權政策</router-link>
        </nav>
      </div>
    </footer>
</template>
