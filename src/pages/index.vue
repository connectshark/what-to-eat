<template>
  <div class="bg-white text-gray-800 font-sans">
    <!-- Hero Section -->
    <header class="bg-gray-50 text-center py-20 sm:py-24">
      <div class="container mx-auto px-4">
        <h1 class="text-4xl sm:text-5xl md:text-6xl font-extrabold text-gray-900 leading-tight mb-4">
          還在煩惱午餐、晚餐吃什麼嗎？
        </h1>
        <p class="text-lg sm:text-xl text-gray-600 max-w-2xl mx-auto mb-8">
          讓「What To Eat」終結您的選擇困難。透過智慧 AI 和簡單選項，立即獲得最適合您的用餐建議。
        </p>
        <router-link to="/discover" class="bg-blue-600 text-white font-bold py-3 px-8 rounded-full hover:bg-blue-700 transition duration-300 ease-in-out transform hover:scale-105">
          立即尋找美食
        </router-link>
      </div>
    </header>

    <!-- Main Content -->
    <main class="py-16 sm:py-20">
      <!-- Features Section -->
      <section class="container mx-auto px-4">
        <h2 class="text-3xl sm:text-4xl font-bold text-center text-gray-900 mb-12">
          探索強大功能
        </h2>
        <div class="grid md:grid-cols-3 gap-8 text-center">
          <div class="bg-gray-50 p-8 rounded-xl shadow-sm">
            <h3 class="text-xl font-semibold text-gray-900 mb-3">智慧 AI 推薦</h3>
            <p class="text-gray-600">
              我們的 AI 會根據您的心情、預算和飲食偏好，提供個人化的餐點建議。
            </p>
          </div>
          <div class="bg-gray-50 p-8 rounded-xl shadow-sm">
            <h3 class="text-xl font-semibold text-gray-900 mb-3">簡單快速</h3>
            <p class="text-gray-600">
              只需幾個點擊，就能從無數的選項中解脫，把時間花在更重要的事情上。
            </p>
          </div>
          <div class="bg-gray-50 p-8 rounded-xl shadow-sm">
            <h3 class="text-xl font-semibold text-gray-900 mb-3">多樣化選擇</h3>
            <p class="text-gray-600">
              從家常菜到異國料理，從健康輕食到豐盛大餐，滿足您所有的味蕾想像。
            </p>
          </div>
        </div>
      </section>

      <!-- How It Works Section -->
      <section class="bg-white py-16 sm:py-20 mt-16">
        <div class="container mx-auto px-4">
          <h2 class="text-3xl sm:text-4xl font-bold text-center text-gray-900 mb-12">
            三步驟，輕鬆搞定
          </h2>
          <div class="flex flex-col md:flex-row justify-around items-center text-center gap-8">
            <div class="flex flex-col items-center">
              <div class="bg-blue-600 text-white w-12 h-12 rounded-full flex items-center justify-center text-xl font-bold mb-4">1</div>
              <h3 class="text-xl font-semibold text-gray-900 mb-2">告訴我們您的偏好</h3>
              <p class="text-gray-600 max-w-xs">選擇您的預算、口味、想吃的料理類型。</p>
            </div>
            <div class="flex flex-col items-center">
              <div class="bg-blue-600 text-white w-12 h-12 rounded-full flex items-center justify-center text-xl font-bold mb-4">2</div>
              <h3 class="text-xl font-semibold text-gray-900 mb-2">獲得 AI 即時建議</h3>
              <p class="text-gray-600 max-w-xs">我們的系統會立刻為您生成數個餐點選項。</p>
            </div>
            <div class="flex flex-col items-center">
              <div class="bg-blue-600 text-white w-12 h-12 rounded-full flex items-center justify-center text-xl font-bold mb-4">3</div>
              <h3 class="text-xl font-semibold text-gray-900 mb-2">享受您的美味時光</h3>
              <p class="text-gray-600 max-w-xs">不再猶豫，立即前往或訂購您的下一餐。</p>
            </div>
          </div>
        </div>
      </section>
    </main>

    
  </div>
</template>

<script setup>
// This script block is intentionally left blank for this static landing page.
// Future interactivity can be added here.
</script>