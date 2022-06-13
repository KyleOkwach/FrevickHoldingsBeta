<script>
// import { ref } from 'vue'
let image = 1
export default{
    name: 'Hero',
    methods: {
        
    },
    mounted() {
        
    },

    setup() {
      return {
        image
      }
    }
}
</script>

<template>
  <div class="hero h-[100vh] 
    bg-[url('./images/hero/1.jpg')] bg-cover bg-center text-white "
    :class=" 'bg' "
  >
    <div class="bg-black w-full 
      h-full bg-opacity-50 
      transition-all duration-1000 gap-56
      flex items-center p-10 pl-20 text-left"
    >
      <div class="flex flex-col justify-items-start">
        <h1 class="uppercase font-bold text-2xl sm:text-5xl">Find what you need</h1>
        <h3 class="text-xl">Explore a variety of the products that we offer</h3>
        <button @click="scrollToElement('main')"
        class="p-4 w-32 rounded-[2px] outline
         hover:bg-white hover:text-gray-900 mt-8
         transition-all duration-500 outline-white outline-2 "
        >
          Explore
        </button>
      </div>
    </div>
  </div>
</template>
