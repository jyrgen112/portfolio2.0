<template>
    <div class="projects-page bg-gray-800 min-h-screen text-white">
      <div class="projects p-8">
        <h1 class="text-4xl font-bold text-center mb-6">Projects</h1>
  
        <!-- Navigation buttons -->
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
  
        <!-- Project Containers (each slide shows one project) -->
        <div class="slider-container overflow-hidden relative">
          <div class="slider flex space-x-4" :style="{ transform: `translateX(-${currentIndex * 100}%)` }">
            <div class="project-container p-4 bg-gray-700 rounded-lg text-center flex-shrink-0 w-full">
              <img src="/home/jurgen/portfolio/portfolio/src/components/imgs/Kuvatõmmis 2024-11-20 103040.png" alt="Project 1" class="w-full h-auto rounded-lg mb-4">
              <h3 class="text-xl font-semibold text-white">Project 1</h3>
              <p class="text-gray-300">1st project where we had to code a similimer site we were given</p>
            </div>
  
            <div class="project-container p-4 bg-gray-700 rounded-lg text-center flex-shrink-0 w-full">
              <img src="/home/jurgen/portfolio/portfolio/src/components/imgs/Kuvatõmmis 2024-11-20 103452.png" alt="Project 2" class="w-full h-auto rounded-lg mb-4">
              <h3 class="text-xl font-semibold text-white">Project 2</h3>
              <p class="text-gray-300">We had to code a card so when u hover over it it would flip</p>
            </div>
  
            <div class="project-container p-4 bg-gray-700 rounded-lg text-center flex-shrink-0 w-full">
              <img src="https://via.placeholder.com/800x400" alt="Project 3" class="w-full h-auto rounded-lg mb-4">
              <h3 class="text-xl font-semibold text-white">Project 3</h3>
              <p class="text-gray-300">Description of Project 3</p>
            </div>
  
            <div class="project-container p-4 bg-gray-700 rounded-lg text-center flex-shrink-0 w-full">
              <img src="https://via.placeholder.com/800x400" alt="Project 4" class="w-full h-auto rounded-lg mb-4">
              <h3 class="text-xl font-semibold text-white">Project 4</h3>
              <p class="text-gray-300">Description of Project 4</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'Projects',
    data() {
      return {
        currentIndex: 0, // Track the current position of the slider
      };
    },
    methods: {
      moveLeft() {
        // Move left (ensure we don't go out of bounds)
        if (this.currentIndex > 0) {
          this.currentIndex--;
        }
      },
      moveRight() {
        // Move right (ensure we don't go out of bounds)
        if (this.currentIndex < 3) { // Maximum 3 because we have 4 items
          this.currentIndex++;
        }
      },
    },
  };
  </script>
  
  <style scoped>
  /* Make the entire page background the dark color */
  .projects-page {
    background-color: #2d3748; /* Dark gray background color */
    min-height: 100vh; /* Ensure the page takes full height */
  }
  
  /* Style the content section of the Projects page */
  .projects {
    max-width: 900px;
    margin: 0 auto;
    background-color: #2d3748; /* Background for content area */
    padding: 20px;
    border-radius: 10px;
  }
  
  /* Slider container with overflow hidden */
  .slider-container {
    max-width: 100%;
    position: relative;
    overflow: hidden;
  }
  
  /* The slider itself */
  .slider {
    display: flex;
    transition: transform 0.5s ease; /* Smooth transition */
  }
  
  /* Each project container */
  .project-container {
    flex-shrink: 0; /* Prevent images from shrinking */
    width: 100%; /* Make each container take 100% width (only one project visible at a time) */
    text-align: center;
  }
  
  .project-container img {
    transition: transform 0.3s ease;
  }
  
  .project-container:hover img {
    transform: scale(1.05); /* Add a zoom effect on hover */
  }
  
  button {
    font-size: 1.1rem;
    cursor: pointer;
  }
  
  button:hover {
    background-color: #444;
  }
  </style>
  