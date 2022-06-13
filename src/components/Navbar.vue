<script>
import { ref } from 'vue'


export default{
    name: 'Navbar',
    props: {},
    setup() {
        let colorBg = ref(false)

        document.addEventListener("scroll", function(){
            let bodyTop = document.body.getBoundingClientRect().top

            if (bodyTop < -150) {
                colorBg.value = true
            } else {
                colorBg.value = false
            }
        })

        return {
            colorBg
        }
    }
}
</script>

<template>
    <nav id="navbar"
        class="fixed flex justify-between items-center
        h-12  text-white w-full pl-12 pr-12 bg-gray-700 shadow
        transtion-color duration-300"
        :class="{ 'bg-transparent shadow-none h-16' : !colorBg }"
    >
        <a href="">
            <h1 class="text-3xl font-bold uppercase">
                Frevick Holdings
            </h1>
        </a>
        <ul class="flex gap-4">
            <li class="hover:bg-white hover:shadow-sm hover:text-gray-900 p-1 rounded-[5px] transition-all duration-300"><a href="">Products</a></li>
            <li class="hover:bg-white hover:shadow-sm hover:text-gray-900 p-1 rounded-[5px] transition-all duration-300"><a href="">FAQs</a></li>
            <li class="hover:bg-white hover:shadow-sm hover:text-gray-900 p-1 rounded-[5px] transition-all duration-300"><a href="">Contacts</a></li>
            <li class="hover:bg-white hover:shadow-sm hover:text-gray-900 p-1 rounded-[5px] transition-all duration-300"><a href=""><i class="fa-solid fa-cart-plus"></i></a></li>
        </ul>
    </nav>
</template>

<style>
nav{
    z-index: 12;
} 
</style>