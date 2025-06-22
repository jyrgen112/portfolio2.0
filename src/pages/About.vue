<template>
    <div class="about-page bg-gray-800 min-h-screen text-white">
      <div class="about-content p-8">
        <h1 class="text-4xl font-bold text-center mb-6">About Me</h1>
        
        <div class="description mb-8">
          <p class="text-lg">
            My name is <strong>Jürgen Vander</strong>, and I am a beginner web developer. I have been learning coding for 2 years at <strong>Kuresaare Ametikool</strong>. I try to learn something new about coding every day.
          </p>
          <p class="text-lg mt-4">
            I am also an active member of the <strong>Estonian Defence Legion</strong>, and I maintain a healthy lifestyle by being an active person in the gym. I used to play tennis for 7 years, and I always try to stay engaged in physical activities.
          </p>
        </div>
  
        <div class="images flex justify-around gap-8 mb-8">
          <div class="image-container w-1/4">
            <img 
<<<<<<< HEAD
              src="/home/jurgen/portfolio2.0/public/imgs/OF.jpg" 
=======
              src="/home/jurgen/portfolio2.0/src/components/imgs/ofitlight.png" 
>>>>>>> 6eb6d79c6b424707202b3a1187bb91b5d27ee462
              alt="Jürgen Vander" 
              class="w-full h-auto rounded-lg shadow-lg"
            />
            <p class="text-center mt-2">Jürgen Vander</p>
          </div>

          <div class="image-container w-1/4">
            <img 
<<<<<<< HEAD
              src="/home/jurgen/portfolio2.0/public/imgs/KL.png" 
=======
              src="/home/jurgen/portfolio2.0/src/components/imgs/KL.png   " 
>>>>>>> 6eb6d79c6b424707202b3a1187bb91b5d27ee462
              alt="Estonian Defence Legion" 
              class="w-full h-auto rounded-lg shadow-lg"
            />
            <p class="text-center mt-2">Estonian Defence Legion</p>
          </div>
  
          <div class="image-container w-1/4">
            <img 
<<<<<<< HEAD
              src="/home/jurgen/portfolio2.0/public/imgs/gym.png" 
=======
              src="/home/jurgen/portfolio2.0/src/components/imgs/gym.png" 
>>>>>>> 6eb6d79c6b424707202b3a1187bb91b5d27ee462
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

  .about-page {
    background-color: #2d3748; 
    min-height: 100vh;
  }
  
  .about-content {
    max-width: 900px;
    margin: 0 auto;
    padding: 20px;
    background-color: #2d3748; 
    border-radius: 10px;
  }
  
  .description {
    text-align: center;
  }
  
  .image-container img {
    transition: transform 0.3s ease;
  }
  
  .image-container img:hover {
    transform: scale(1.05); 
  }
  
  .images {
    display: flex;
    justify-content: space-around;
    gap: 20px;
  }
  
  .image-container p {
    font-size: 1rem;
    color: #e2e8f0; 
  }
  </style>
  