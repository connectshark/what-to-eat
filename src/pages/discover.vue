<template>
  <div class="bg-gray-50 min-h-screen font-sans">
    <div class="container mx-auto px-4 py-12">
      <div class="max-w-4xl mx-auto">
        <h1 class="text-4xl font-bold text-gray-900 text-center mb-4">尋找您的下一餐</h1>
        <p class="text-lg text-gray-600 text-center mb-10">請勾選您的偏好，讓 AI 為您推薦最棒的選擇。</p>

        <!-- Filters Section -->
        <div class="bg-white p-8 rounded-xl shadow-md mb-10">
          <div class="space-y-8">
            <!-- Budget Filter -->
            <div>
              <h3 class="text-lg font-medium text-gray-900 mb-4">您的預算？</h3>
              <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
                <div v-for="option in budgetOptions" :key="option.id">
                  <label class="flex items-center p-3 border border-gray-200 rounded-lg cursor-pointer hover:bg-gray-100">
                    <input type="radio" :value="option.value" v-model="selectedBudget" class="h-4 w-4 text-blue-600 border-gray-300 rounded focus:ring-blue-500">
                    <span class="ml-3 text-sm font-medium text-gray-700">{{ option.label }}</span>
                  </label>
                </div>
              </div>
            </div>

            <!-- Cuisine Type Filter -->
            <div>
              <h3 class="text-lg font-medium text-gray-900 mb-4">想吃什麼類型？</h3>
              <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
                <div v-for="option in cuisineOptions" :key="option.id">
                  <label :for="option.id" class="flex items-center p-3 border border-gray-200 rounded-lg cursor-pointer hover:bg-gray-100">
                    <input :id="option.id" type="checkbox" :value="option.value" v-model="selectedCuisines" class="h-4 w-4 text-blue-600 border-gray-300 rounded focus:ring-blue-500">
                    <span class="ml-3 text-sm font-medium text-gray-700">{{ option.label }}</span>
                  </label>
                </div>
              </div>
            </div>

            <!-- Mood Filter -->
            <div>
              <h3 class="text-lg font-medium text-gray-900 mb-4">今天心情如何？</h3>
              <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
                <div v-for="option in moodOptions" :key="option.id">
                  <label :for="option.id" class="flex items-center p-3 border border-gray-200 rounded-lg cursor-pointer hover:bg-gray-100">
                    <input :id="option.id" type="checkbox" :value="option.value" v-model="selectedMoods" class="h-4 w-4 text-blue-600 border-gray-300 rounded focus:ring-blue-500">
                    <span class="ml-3 text-sm font-medium text-gray-700">{{ option.label }}</span>
                  </label>
                </div>
              </div>
            </div>
          </div>

          <div class="text-center mt-10">
            <button class="bg-blue-600 cursor-pointer text-white font-bold py-3 px-10 rounded-full hover:bg-blue-700 transition duration-300 transform hover:scale-105">
              開始搜尋
            </button>
          </div>
        </div>

        <!-- Results Section -->
        <div class="text-center">
            <h2 class="text-2xl font-bold text-gray-800 mb-6">為您推薦</h2>
            <div class="bg-white p-8 rounded-xl shadow-md">
                <p class="text-gray-500">點擊「開始搜尋」後，您的美食推薦將會顯示在這裡。</p>
            </div>
        </div>

      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

// Budget Options
const budgetOptions = [
  { id: 'budget-1', value: '$', label: '$' },
  { id: 'budget-2', value: '$$', label: '$$' },
  { id: 'budget-3', value: '$$$', label: '$$$' },
  { id: 'budget-4', value: '$$$$', label: '$$$$' },
];
const selectedBudget = ref('')

// Cuisine Options
const cuisineOptions = [
  { id: 'cuisine-1', value: 'chinese', label: '中式' },
  { id: 'cuisine-2', value: 'western', label: '西式' },
  { id: 'cuisine-3', value: 'japanese', label: '日式' },
  { id: 'cuisine-4', value: 'korean', label: '韓式' },
  { id: 'cuisine-5', value: 'italian', label: '義式' },
  { id: 'cuisine-6', value: 'se_asian', label: '東南亞' },
  { id: 'cuisine-7', value: 'fast_food', label: '速食' },
  { id: 'cuisine-8', value: 'other', label: '其他' },
];
const selectedCuisines = ref([]);

// Mood Options
const moodOptions = [
  { id: 'mood-1', value: 'light', label: '想吃點清淡的' },
  { id: 'mood-2', value: 'heavy', label: '想來點重口味' },
  { id: 'mood-3', value: 'comfort', label: '需要一點療癒' },
  { id: 'mood-4', value: 'celebrate', label: '想好好慶祝一下' },
];
const selectedMoods = ref([]);

</script>