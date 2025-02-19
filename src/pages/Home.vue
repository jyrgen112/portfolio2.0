<template>
  <div class="min-h-screen bg-gray-900 text-white flex items-center justify-center px-4 sm:px-6 lg:px-8">
    <div class="text-center max-w-sm sm:max-w-md w-full">
      <h1 class="text-4xl sm:text-5xl font-bold mb-6 leading-tight">
        Web Developer
      </h1>
      
      <div class="space-y-4">
        <p class="text-base sm:text-lg text-gray-300">
          Hello, I am Jurgen Vander
        </p>
        
        <p class="text-base sm:text-lg text-gray-300">
          I am a web developer, currently learning IT at Kuresaare Ametikool
        </p>
      </div>
      
      <div class="mt-8 flex justify-center space-x-4">
        <button 
          class="bg-blue-600 hover:bg-blue-700 text-white px-6 py-2 rounded-lg transition-colors duration-200"
          @click="handleContact"
        >
          Contact Me
        </button>
        <button 
          class="border border-blue-600 text-blue-600 hover:bg-blue-600 hover:text-white px-6 py-2 rounded-lg transition-colors duration-200"
          @click="handlePortfolio"
        >
          Portfolio
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
const handleContact = () => {
  console.log('Contact button clicked')
}

const handlePortfolio = () => {
  console.log('Portfolio button clicked')
}
</script>

<style scoped>
</style>