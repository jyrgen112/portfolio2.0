<template>
  <div class="min-h-screen bg-gray-900 text-white flex items-center justify-center px-4 sm:px-6 lg:px-8">
    <div class="text-center max-w-sm sm:max-w-md w-full">
      <h1 class="text-4xl sm:text-5xl font-bold mb-6 leading-tight typing-text">
        {{ displayedText }}
      </h1>

      <div class="space-y-4">
        <p class="text-base sm:text-lg text-gray-300 fade-in" v-show="showIntro">
          Hello, I am <span class="text-blue-400">Jurgen Vander</span>
        </p>

        <p class="text-base sm:text-lg text-gray-300 slide-in" v-show="showIntro">
          I am a web developer, currently learning IT at Kuressaare Ametikool
        </p>
      </div>

      <div class="mt-8 flex justify-center space-x-4">
        
        <a 
          :href="`mailto:jurgen.vander@ametikool.ee?subject=Let's Connect!&body=Hi Jurgen,`"
          class="bg-blue-600 hover:bg-blue-700 text-white px-6 py-2 rounded-lg transition-colors duration-200 shadow-lg"
        >
          Contact Me
        </a>

        <button 
          class="border border-blue-600 text-blue-600 hover:bg-blue-600 hover:text-white px-6 py-2 rounded-lg transition-colors duration-200 shadow-lg"
          @click="handlePortfolio"
        >
          Portfolio
        </button>
      </div>

      
      <div class="cube-container mt-8">
        <div class="cube">
          <div class="face front"></div>
          <div class="face back"></div>
          <div class="face left"></div>
          <div class="face right"></div>
          <div class="face top"></div>
          <div class="face bottom"></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';

const fullText = "Web Developer";
const displayedText = ref("");
const showIntro = ref(false);

onMounted(() => {
  typeEffect();
  setTimeout(() => {
    showIntro.value = true;
  }, 2000);
});

const typeEffect = () => {
  let index = 0;
  const interval = setInterval(() => {
    if (index < fullText.length) {
      displayedText.value += fullText[index];
      index++;
    } else {
      clearInterval(interval);
    }
  }, 100);
};

const handlePortfolio = () => {
  console.log('Portfolio button clicked');
};
</script>

<style scoped>

.typing-text {
  font-family: monospace;
  white-space: nowrap;
  overflow: hidden;
  border-right: 3px solid white;
  display: inline-block;
  animation: blink 0.7s steps(2, start) infinite;
}

@keyframes blink {
  50% { border-color: transparent; }
}

.cube-container {
  perspective: 1000px;
  width: 100px; 
  height: 100px; 
  position: relative;
  margin: 50px auto;
}

.cube {
  width: 100%;
  height: 100%;
  position: absolute;
  transform-style: preserve-3d;
  animation: spin 5s infinite linear;
}

.face {
  position: absolute;
  width: 100px; 
  height: 100px;
  background: rgba(255, 255, 255, 0.1); 
  border: 1px solid rgba(255, 255, 255, 0.5);
}

.front  { transform: translateZ(50px); }
.back   { transform: rotateY(180deg) translateZ(50px); }
.left   { transform: rotateY(-90deg) translateZ(50px); }
.right  { transform: rotateY(90deg) translateZ(50px); }
.top    { transform: rotateX(90deg) translateZ(50px); }
.bottom { transform: rotateX(-90deg) translateZ(50px); }

@keyframes spin {
  from { transform: rotateX(0deg) rotateY(0deg); }
  to { transform: rotateX(360deg) rotateY(360deg); }
}

.fade-in {
  opacity: 0;
  animation: fade 1.5s ease-in forwards;
}

@keyframes fade {
  to { opacity: 1; }
}

.slide-in {
  opacity: 0;
  transform: translateX(-20px);
  animation: slide 1.5s ease-in forwards;
}

@keyframes slide {
  to {
    opacity: 1;
    transform: translateX(0);
  }
}
</style>