<template>
  <div class="bg-gray-50 min-h-screen font-sans">
    <div class="container mx-auto px-4 py-12">
      <div class="max-w-4xl mx-auto">
        <h1 class="text-4xl font-bold text-gray-900 text-center mb-4">尋找您的下一餐</h1>
        <p class="text-lg text-gray-600 text-center mb-10">請勾選您的偏好，讓 AI 為您推薦最棒的選擇。</p>

        <form @submit.prevent="onSubmit" class="bg-white p-8 rounded-xl shadow-md mb-10">
          <div class="space-y-8">
            <div>
              <h3 class="text-lg font-medium text-gray-900 mb-4">您的預算？</h3>
              <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
                <div v-for="option in budgetOptions" :key="option.id">
                  <label class="flex items-center p-3 border border-gray-200 rounded-lg cursor-pointer hover:bg-gray-100">
                    <input required type="radio" name="budget" :value="option.value" v-model="selectedBudget" class="sr-only peer">
                    <span class="peer-checked:hidden">
                      <i class='bx bx-sm bx-radio-circle'></i> 
                    </span>
                    <span class="peer-checked:inline hidden">
                      <i class='bx bx-sm bx-radio-circle-marked'></i> 
                    </span>
                    <span class="font-medium text-gray-700">
                      <i v-for="star in option.label" :key="star" class='bx bx-sm bx-dollar'></i> 
                    </span>
                  </label>
                </div>
              </div>
            </div>

            <div>
              <h3 class="text-lg font-medium text-gray-900 mb-4">想吃什麼類型？</h3>
              <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
                <div v-for="option in cuisineOptions" :key="option.id">
                  <label class="flex items-center p-3 border border-gray-200 rounded-lg cursor-pointer hover:bg-gray-100">
                    <input type="checkbox" name="cuisines" :value="option.value" v-model="selectedCuisines" class="sr-only peer">
                    <span class="peer-checked:hidden">
                      <i class='bx bx-sm bx-square-rounded'></i>
                    </span>
                    <span class="peer-checked:inline hidden">
                      <i class='bx bx-sm bx-check-square'  ></i> 
                    </span>
                    <span class="ml-3 text-sm font-medium text-gray-700">{{ option.label }}</span>
                  </label>
                </div>
              </div>
            </div>

            <div>
              <h3 class="text-lg font-medium text-gray-900 mb-4">今天心情如何？</h3>
              <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
                <div v-for="option in moodOptions" :key="option.id">
                  <label class="flex items-center p-3 border border-gray-200 rounded-lg cursor-pointer hover:bg-gray-100">
                    <input type="checkbox" name="moods" :value="option.value" v-model="selectedMoods" class="sr-only peer">
                    <span class="peer-checked:hidden">
                      <i class='bx bx-sm bx-square-rounded'></i>
                    </span>
                    <span class="peer-checked:inline hidden">
                      <i class='bx bx-sm bx-check-square'  ></i> 
                    </span>
                    <span class="ml-3 text-sm font-medium text-gray-700">{{ option.label }}</span>
                  </label>
                </div>
              </div>
            </div>
          </div>

          <div class="text-center mt-10">
            <button :disabled="loading" type="submit" class="bg-blue-600 cursor-pointer text-white font-bold py-3 px-10 rounded-full hover:bg-blue-700 transition duration-300 transform hover:scale-105 disabled:bg-gray-500 disabled:cursor-not-allowed">
              開始搜尋
            </button>
          </div>
        </form>

        <div class="text-center">
          <h2 class="text-2xl font-bold text-gray-800 mb-6">為您推薦</h2>
          <div class="bg-white p-8 rounded-xl shadow-md">
            <p v-if="loading"><i class='bx bx-sm bx-loader-lines'></i>正在運算中，請稍候...</p>
            <article class="prose" v-else-if="result" v-html="result"></article>
            <p v-else class="text-gray-500">點擊「開始搜尋」後，您的美食推薦將會顯示在這裡。</p>
          </div>
        </div>

      </div>
    </div>
  </div>
</template>

<script setup>
import MarkdownIt from 'markdown-it'
import { ref } from 'vue'

const budgetOptions = [
  { id: 'budget-1', value: '低', label: 1 },
  { id: 'budget-2', value: '中', label: 2 },
  { id: 'budget-3', value: '高', label: 3 },
  { id: 'budget-4', value: '頂級', label: 4 },
];
const selectedBudget = ref('')

const cuisineOptions = [
  { id: 'cuisine-1', value: '中式', label: '中式' },
  { id: 'cuisine-2', value: '西式', label: '西式' },
  { id: 'cuisine-3', value: '日式', label: '日式' },
  { id: 'cuisine-4', value: '韓式', label: '韓式' },
  { id: 'cuisine-5', value: '義式', label: '義式' },
  { id: 'cuisine-6', value: '東南亞', label: '東南亞' },
  { id: 'cuisine-7', value: '速食', label: '速食' },
  { id: 'cuisine-8', value: '其他', label: '其他' },
];
const selectedCuisines = ref([])

const moodOptions = [
  { id: 'mood-1', value: '清淡', label: '想吃點清淡的' },
  { id: 'mood-2', value: '重', label: '想來點重口味' },
  { id: 'mood-3', value: '療癒', label: '需要一點療癒' },
  { id: 'mood-4', value: '慶祝', label: '想好好慶祝一下' },
];
const selectedMoods = ref([])

const API_URI = import.meta.env.VITE_API_URI

const md = MarkdownIt()
const loading = ref(false)
const result = ref('')
const onSubmit = async () => {
  loading.value = true
  const cuisines = selectedCuisines.value.length ? selectedCuisines.value.join(',') : '沒特別要求'
  const moods = selectedMoods.value.length ? selectedMoods.value.join(',') : '沒特別'
  const prompt = `推薦我一個用餐時候的料理選擇，我的預算是${ selectedBudget.value }價位，我可以選的料理類型是${ cuisines }，我的心情是${ moods }，用繁體中文回答我`
  const url = `${ API_URI }/text/${ encodeURIComponent(prompt) }`
  const response = await fetch(url)
    .catch(error => {
      console.error('Error:', error)
      result.value = '發生錯誤，請稍後再試'
      loading.value = false
      return
    })
  const data = await response.json()
  result.value = md.render(data)
  loading.value = false
}
</script>