<template>
    <div class="about-page bg-gray-800 min-h-screen text-white">
      <div class="about-content p-8">
        <h1 class="text-4xl font-bold text-center mb-6">About Me</h1>
        
        <!-- Personal Description -->
        <div class="description mb-8">
          <p class="text-lg">
            My name is <strong>Jürgen Vander</strong>, and I am a beginner web developer. I have been learning coding for 2 years at <strong>Kuresaare Ametikool</strong>. I try to learn something new about coding every day.
          </p>
          <p class="text-lg mt-4">
            I am also an active member of the <strong>Estonian Defence Legion</strong>, and I maintain a healthy lifestyle by being an active person in the gym. I used to play tennis for 7 years, and I always try to stay engaged in physical activities.
          </p>
        </div>
  
        <!-- Images -->
        <div class="images flex justify-around gap-8 mb-8">
          <!-- Image 1: Your Photo -->
          <div class="image-container w-1/4">
            <img 
              src="/home/jurgen/portfolio2.0/public/imgs/OF.jpg" 
              alt="Jürgen Vander" 
              class="w-full h-auto rounded-lg shadow-lg"
            />
            <p class="text-center mt-2">Jürgen Vander</p>
          </div>
  
          <!-- Image 2: Estonia Defence Legion -->
          <div class="image-container w-1/4">
            <img 
              src="/home/jurgen/portfolio2.0/public/imgs/KL.png" 
              alt="Estonian Defence Legion" 
              class="w-full h-auto rounded-lg shadow-lg"
            />
            <p class="text-center mt-2">Estonian Defence Legion</p>
          </div>
  
          <!-- Image 3: Gym -->
          <div class="image-container w-1/4">
            <img 
              src="/home/jurgen/portfolio2.0/public/imgs/gym.png" 
              alt="Gym" 
              class="w-full h-auto rounded-lg shadow-lg"
            />
            <p class="text-center mt-2">Gym Lifestyle</p>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'About',
  };
  </script>
  
  <style scoped>
  /* General page styling */
  .about-page {
    background-color: #2d3748; /* Dark gray background */
    min-height: 100vh;
  }
  
  .about-content {
    max-width: 900px;
    margin: 0 auto;
    padding: 20px;
    background-color: #2d3748; /* Consistent background color */
    border-radius: 10px;
  }
  
  .description {
    text-align: center;
  }
  
  .image-container img {
    transition: transform 0.3s ease;
  }
  
  .image-container img:hover {
    transform: scale(1.05); /* Zoom effect on hover */
  }
  
  .images {
    display: flex;
    justify-content: space-around;
    gap: 20px;
  }
  
  .image-container p {
    font-size: 1rem;
    color: #e2e8f0; /* Light gray for captions */
  }
  </style>
  