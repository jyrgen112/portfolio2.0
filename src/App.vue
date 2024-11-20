<template>
   <div class="bg-gray-800 text-white p-4">
    <nav class="flex justify-between">
      <div class="text-2xl font-bold">My Portfolio</div>
      <div>
        <router-link to="/" class="p-2 hover:bg-gray-700">Home</router-link>
        <router-link to="/about" class="p-2 hover:bg-gray-700">About</router-link>
        <router-link to="/projects" class="p-2 hover:bg-gray-700">Projects</router-link>
        <router-link to="/contact" class="p-2 hover:bg-gray-700">Contact Me</router-link> <!-- Add link here -->
      </div>
    </nav>
  </div>
    <RouterView></RouterView>
  </template>
  
  <script>
  export default {
    name: 'Navbar',
  };
  </script>
  