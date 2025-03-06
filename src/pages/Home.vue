<template>
  <div class="min-h-screen bg-gray-900 text-white flex items-center justify-center px-4 sm:px-6 lg:px-8">
    <div class="text-center max-w-sm sm:max-w-md w-full">
      <!-- Animated Title -->
      <h1 class="text-4xl sm:text-5xl font-bold mb-6 leading-tight typing-text">
        {{ displayedText }}
      </h1>

      <div class="space-y-4">
        <!-- Fade-in animation -->
        <p class="text-base sm:text-lg text-gray-300 fade-in" v-show="showIntro">
          Hello, I am <span class="text-blue-400">Jurgen Vander</span>
        </p>

        <!-- Slide-in animation -->
        <p class="text-base sm:text-lg text-gray-300 slide-in" v-show="showIntro">
          I am a web developer, currently learning IT at Kuressaare Ametikool
        </p>
      </div>

      <div class="mt-8 flex justify-center space-x-4">
        <!-- Contact Button: Opens email client -->
        <a 
          :href="`mailto:jurgen.vander@example.com?subject=Let's Connect!&body=Hi Jurgen,`"
          class="bg-blue-600 hover:bg-blue-700 text-white px-6 py-2 rounded-lg transition-colors duration-200 shadow-lg"
        >
          Contact Me
        </a>

        <!-- Portfolio Button -->
        <button 
          class="border border-blue-600 text-blue-600 hover:bg-blue-600 hover:text-white px-6 py-2 rounded-lg transition-colors duration-200 shadow-lg"
          @click="handlePortfolio"
        >
          Portfolio
        </button>
      </div>

      <!-- 3D Spinning Cube -->
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
/* Typing effect */
.typing-text {
  font-family: monospace;
  white-space: nowrap;
  overflow: hidden;
  border-right: 3px solid white;
  display: inline-block;
  animation: blink 0.7s steps(2, start) infinite;
}

/* Blinking cursor animation */
@keyframes blink {
  50% { border-color: transparent; }
}

/* 3D Cube */
.cube-container {
  perspective: 1000px;
  width: 100px; /* Smaller width */
  height: 100px; /* Smaller height */
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
  width: 100px; /* Smaller width */
  height: 100px; /* Smaller height */
  background: rgba(255, 255, 255, 0.1); /* See-through */
  border: 1px solid rgba(255, 255, 255, 0.5); /* Highlighted square lines */
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

/* Fade-in effect */
.fade-in {
  opacity: 0;
  animation: fade 1.5s ease-in forwards;
}

@keyframes fade {
  to { opacity: 1; }
}

/* Slide-in effect */
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