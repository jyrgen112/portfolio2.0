<template>
  <div class="relative min-h-screen bg-gray-900 text-white">
    <!-- Navigation Bar -->
    <nav class="fixed top-0 left-0 right-0 z-50 bg-gray-900/80 backdrop-blur-sm">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="flex items-center justify-between h-16">
          <div class="flex items-center">
            <span class="text-xl font-bold">JV</span>
          </div>
          <div class="flex space-x-4">
            <button 
              @click="scrollToSection('about')"
              class="text-gray-300 hover:text-white px-3 py-2 rounded-md text-sm font-medium transition-colors duration-200"
            >
              About
            </button>
            <button 
              @click="router.push('/portfolio')"
              class="text-gray-300 hover:text-white px-3 py-2 rounded-md text-sm font-medium transition-colors duration-200"
            >
              Projects
            </button>
            <button 
              @click="router.push('/contact')"
              class="text-gray-300 hover:text-white px-3 py-2 rounded-md text-sm font-medium transition-colors duration-200"
            >
              Contact Me
            </button>
          </div>
        </div>
      </div>
    </nav>

    <canvas ref="matrix" class="fixed top-0 left-0 w-full h-full opacity-40"></canvas>
    
    <!-- Home Section -->
    <div class="min-h-screen flex items-center justify-center px-4 sm:px-6 lg:px-8">
      <div 
        class="text-center max-w-sm sm:max-w-md w-full relative z-10 transition-all duration-700"
        :class="{ 'opacity-0 translate-y-[-100px]': scrollPosition > 300 }"
      >
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

    <!-- About Section -->
    <div 
      id="about"
      class="min-h-screen relative z-10 transition-all duration-700"
      :class="{ 'opacity-100 translate-y-0': scrollPosition > 300, 'opacity-0 translate-y-[100px]': scrollPosition <= 300 }"
    >
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
          <div v-for="(image, index) in images" :key="index" class="image-container w-1/4">
            <img 
              :src="image.src" 
              :alt="image.alt" 
              class="w-full h-auto rounded-lg shadow-lg transition-transform duration-300 hover:scale-105"
            />
            <p class="text-center mt-2">{{ image.caption }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { useRouter } from 'vue-router'
import { onMounted, ref, onUnmounted } from 'vue'

const router = useRouter()
const matrix = ref(null)
const scrollPosition = ref(0)

const images = [
  {
    src: '/imgs/OF.jpg',
    alt: 'Jürgen Vander',
    caption: 'Jürgen Vander'
  },
  {
    src: '/imgs/KL.png',
    alt: 'Estonian Defence Legion',
    caption: 'Estonian Defence Legion'
  },
  {
    src: '/imgs/gym.png',
    alt: 'Gym',
    caption: 'Gym Lifestyle'
  }
]

const scrollToSection = (sectionId) => {
  const element = document.getElementById(sectionId)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
}

const handleScroll = () => {
  scrollPosition.value = window.scrollY
}

const handleContact = () => {
  router.push('/contact')
}

const handlePortfolio = () => {
  router.push('/portfolio')
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
  const canvas = matrix.value
  const ctx = canvas.getContext('2d')
  
  // Set canvas size to match window size
  const resizeCanvas = () => {
    canvas.width = window.innerWidth
    canvas.height = window.innerHeight
  }
  resizeCanvas()
  window.addEventListener('resize', resizeCanvas)
  
  const chars = '0123456789ABCDEF'
  const fontSize = 14
  const columns = canvas.width / fontSize
  
  class Drop {
    constructor(x) {
      this.x = x
      this.y = 0
      this.z = Math.random() * 20
      this.speed = 0.3 + (this.z / 30) // Reduced base speed and divided z influence
      this.char = chars[Math.floor(Math.random() * chars.length)]
    }

    update() {
      this.y += this.speed
      if (this.y * fontSize > canvas.height) {
        this.y = 0
        this.z = Math.random() * 20
        this.speed = 0.3 + (this.z / 30) // Match the new speed calculation
      }
      if (Math.random() > 0.95) {
        this.char = chars[Math.floor(Math.random() * chars.length)]
      }
    }

    draw() {
      const scale = 1 + (this.z / 20) // Larger if closer
      const alpha = 0.1 + (this.z / 20) // More visible if closer
      const posX = this.x * fontSize * (1 + this.z / 50) // X position affected by depth
      
      ctx.font = `${fontSize * scale}px monospace`
      ctx.fillStyle = `rgba(0, 255, 0, ${alpha})`
      ctx.fillText(this.char, posX, this.y * fontSize)
    }
  }

  const drops = Array(Math.floor(columns)).fill().map((_, i) => new Drop(i))
  
  function draw() {
    ctx.fillStyle = 'rgba(0, 0, 0, 0.05)'
    ctx.fillRect(0, 0, canvas.width, canvas.height)
    
    drops.forEach(drop => {
      drop.update()
      drop.draw()
    })
    
    requestAnimationFrame(draw)
  }
  
  draw()
})
</script>

<style scoped>
.perspective {
  transform: perspective(1000px) rotateX(5deg);
}
</style>
