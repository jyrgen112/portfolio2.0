<template>
    <div class="border rounded-lg shadow-md p-4">
      <img :src="image" alt="Project" class="rounded-md mb-4">
      <h3 class="text-xl font-bold">{{ title }}</h3>
      <p class="text-gray-700">{{ description }}</p>
      <a :href="link" class="text-blue-500 hover:underline mt-2 block">View Project</a>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      title: String,
      description: String,
      image: String,
      link: String,
    },
  };
  </script>
  