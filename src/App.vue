<template>
  <nav class="bg-orange-500 p-2 flex items-center gap-4">
    <img src="../public/fox.png" class="w-20" />
    <h2 class="text-white">{{ title }}</h2>
  </nav>

  <main>
    <br />
    <div class="card-container flex flex-wrap gap-4 justify-evenly p-4">
      <div v-for="(fox, index) in galleries" :key="index" class="card m-4 w-64">
        <img :src="fox.image" class="w-full rounded-lg" alt="Fox Image" />
        <h2 class="mt-2 font-bold text-center">Random Fox {{ index + 1 }}</h2>
      </div>
    </div>


    <div class="block m-auto text-center">
          <button
      class="relative inline-flex items-center justify-center px-8 py-2.5 overflow-hidden tracking-tighter text-white bg-gray-800 rounded-md group"
      @click="loadFoxes"
    >
      <span
        class="absolute w-0 h-0 transition-all duration-500 ease-out bg-orange-600 rounded-full group-hover:w-56 group-hover:h-56"
      ></span>
      <span class="absolute bottom-0 left-0 h-full -ml-2">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          class="w-auto h-full opacity-100 object-stretch"
          viewBox="0 0 487 487"
        >
          <path
            fill-opacity=".1"
            fill-rule="nonzero"
            fill="#FFF"
            d="M0 .3c67 2.1 134.1 4.3 186.3 37 52.2 32.7 89.6 95.8 112.8 150.6 23.2 54.8 32.3 101.4 61.2 149.9 28.9 48.4 77.7 98.8 126.4 149.2H0V.3z"
          ></path>
        </svg>
      </span>
      <span class="absolute top-0 right-0 w-12 h-full -mr-3">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          class="object-cover w-full h-full"
          viewBox="0 0 487 487"
        >
          <path
            fill-opacity=".1"
            fill-rule="nonzero"
            fill="#FFF"
            d="M487 486.7c-66.1-3.6-132.3-7.3-186.3-37s-95.9-85.3-126.2-137.2c-30.4-51.8-49.3-99.9-76.5-151.4C70.9 109.6 35.6 54.8.3 0H487v486.7z"
          ></path>
        </svg>
      </span>
      <span
        class="absolute inset-0 w-full h-full -mt-1 rounded-lg opacity-30 bg-gradient-to-b from-transparent via-transparent to-gray-200"
      ></span>
      <span class="relative text-base font-semibold">Load New Foxes 🦊</span>
    </button>
    </div>
  </main>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      title: "Fox Gallery Photos 🦊",
      galleries: [],
    };
  },
  methods: {
    async loadFoxes() {
      this.galleries = [];

      // Load 5 random fox images
      for (let i = 0; i < 15; i++) {
        const response = await fetch("https://randomfox.ca/floof/");
        const data = await response.json();
        this.galleries.push({ image: data.image });
      }
    },
  },
  mounted() {
    this.loadFoxes();
  },
};
</script>
