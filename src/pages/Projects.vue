<template>
  <div class="projects-page bg-gray-800 min-h-screen text-white">
    <div class="projects p-8">
      <h1 class="text-4xl font-bold text-center mb-6">Projects</h1>

      <div class="flex justify-between mb-6">
        <button 
          @click="moveLeft" 
          class="px-4 py-2 bg-gray-700 text-white rounded-lg shadow-lg hover:bg-gray-600 transition">
          ← Previous
        </button>
        <button 
          @click="moveRight" 
          class="px-4 py-2 bg-gray-700 text-white rounded-lg shadow-lg hover:bg-gray-600 transition">
          Next →
        </button>
      </div>

      <div class="slider-container overflow-hidden relative">
        <div class="slider flex space-x-4" :style="{ transform: `translateX(-${currentIndex * 100}%)` }">
          <div class="project-container p-4 bg-gray-700 rounded-lg text-center flex-shrink-0 w-full">
            <img :src="aiStartup" alt="Project 1" class="w-full h-auto rounded-lg mb-4">
            <h3 class="text-xl font-semibold text-white">Project 1</h3>
            <p class="text-gray-300">1st project where we had to code a similar site we were given</p>
          </div>

          <div class="project-container p-4 bg-gray-700 rounded-lg text-center flex-shrink-0 w-full">
            <img :src="cardImg" alt="Project 2" class="w-full h-auto rounded-lg mb-4">
            <h3 class="text-xl font-semibold text-white">Project 2</h3>
            <p class="text-gray-300">We had to code a card so when you hover over it, it would flip</p>
          </div>

          <div class="project-container p-4 bg-gray-700 rounded-lg text-center flex-shrink-0 w-full">
            <img src="/home/jurgen/portfolio2.0/src/components/imgs/tetris.png" alt="Project 3" class="w-full h-auto rounded-lg mb-4">
            <h3 class="text-xl font-semibold text-white">Project tetris</h3>
            <p class="text-gray-300">for the tetris project we had to make a tetris game with css, html and js.</p>
          </div>

          <div class="project-container p-4 bg-gray-700 rounded-lg text-center flex-shrink-0 w-full">
            <img src="/home/jurgen/portfolio2.0/src/components/imgs/snake.png" alt="Project 4" class="w-full h-auto rounded-lg mb-4">
            <h3 class="text-xl font-semibold text-white">Project snake</h3>
            <p class="text-gray-300">In the snake project we had to make a snake game with js, html and css.</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import aiStartup from '@/components/imgs/ai-startup.png';
import cardImg from '@/components/imgs/card.png';

export default {
  name: 'Projects',
  data() {
    return {
      currentIndex: 0,
      aiStartup, 
      cardImg
    };
  },
  methods: {
    moveLeft() {
      if (this.currentIndex > 0) {
        this.currentIndex--;
      }
    },
    moveRight() {
      if (this.currentIndex < 3) { 
        this.currentIndex++;
      }
    }
  }
};
</script>
