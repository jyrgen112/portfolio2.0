<template>
    <div class="contact p-8 text-center">
      <h1 class="text-4xl font-bold text-white mb-6">Contact Me</h1>
      
      <!-- Email -->
      <p class="text-xl text-gray-300 mb-6">
        Email: <a href="mailto:jyrgen.vander@gmail.com" class="text-blue-400 hover:underline">jyrgen.vander@gmail.com</a>
      </p>
  
      <!-- Simple Contact Form -->
      <h2 class="text-2xl font-medium text-gray-200 mb-4">Or send me a message</h2>
      <form @submit.prevent="submitForm" class="max-w-xl mx-auto">
        <div class="mb-4">
          <input type="text" v-model="name" placeholder="Your Name" class="w-full p-3 rounded-md text-black" required />
        </div>
        <div class="mb-4">
          <input type="email" v-model="email" placeholder="Your Email" class="w-full p-3 rounded-md text-black" required />
        </div>
        <div class="mb-4">
          <textarea v-model="message" placeholder="Your Message" rows="5" class="w-full p-3 rounded-md text-black" required></textarea>
        </div>
        <button type="submit" class="w-full bg-blue-600 text-white p-3 rounded-md hover:bg-blue-700">
          Send Message
        </button>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    name: 'Contact',
    data() {
      return {
        name: '',
        email: '',
        message: '',
      };
    },
    methods: {
      submitForm() {
        // Add form submission logic here
        alert(`Message sent by: ${this.name}`);
        // Optionally, you can add email service integration here
        this.name = '';
        this.email = '';
        this.message = '';
      },
    },
  };
  </script>
  
  <style scoped>
  .contact {
    max-width: 800px;
    margin: 0 auto;
  }
  </style>
  