<script>
    import { ref } from 'vue'

    export default{
        name: 'Footer'
    }
</script>

<template>
  <!-- FOOTER -->
  <div class="h-20 bg-gray-800 text-white mt-5 flex flex-col gap-2 items-center">
    <div class="flex items-center justify-center">
      <p>Frevick Holdings&trade;</p>
    </div>
    <hr class="bg-gray-800 w-[98%]"/>
    <div>
      <ul class="flex gap-2">
        <li class="hover:text-green-500"><a href="">Contact Us</a></li>
        <li class="hover:text-green-500"><a href="">Follow Us</a></li>
      </ul>
    </div>
  </div>
</template>