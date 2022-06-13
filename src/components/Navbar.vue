<script>
import { ref } from 'vue'
import Cart from './Cart.vue';


export default{
    name: "Navbar",
    setup() {
        let colorBg = ref(false);
        document.addEventListener("scroll", function () {
            let bodyTop = document.body.getBoundingClientRect().top;
            if (bodyTop < -50) {
                colorBg.value = true;
            }
            else {
                colorBg.value = false;
            }

        });
        return {
            colorBg
        };
    },
    data() {
        return {
            displayCart: false
        }
    },
    props: {
        inCart: 0,
        mCart: []
    },
    methods: {
        toggleCart() {
            this.displayCart = !this.displayCart;
        }
    },
    components: { Cart }
}
</script>

<template>
    <nav id="navbar"
        class="fixed flex justify-between items-center
        h-12  text-white w-full pl-12 pr-12 bg-gray-700 shadow
        transtion-color duration-300"
        :class="{ 'bg-transparent shadow-none h-16' : !colorBg }"
    >
        <a href="./">
            <h1 class=" sm:text-3xl font-bold uppercase">
                Frevick Holdings
            </h1>
        </a>
        <ul class="sm:flex gap-4">
            <li class=" hover:text-gray-900 p-1 
                flex transition-all duration-300
                justify-center items-center
            ">
                <button @click="toggleCart">
                    <i class="fa-solid fa-cart-arrow-down"></i>
                    <sup v-if="inCart >= 1" class="relative right-1 bg-green-600 rounded-[100%] p-[1px] px-[4px]">{{ inCart }}</sup>
                </button>
            </li>
        </ul>
    </nav>

    <Cart :myCart="mCart" v-if="displayCart" class="transition-all duration-500" />

</template>

<style>
nav{
    z-index: 12;
} 
</style>