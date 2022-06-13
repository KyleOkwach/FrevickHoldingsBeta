<script>
import { ref } from "vue"

export default({
    name: 'Cart',
    props: {
        myCart: [],
    },
    methods: {
        removeFromCart(product){
            this.myCart.splice(this.myCart.indexOf(product))
        }
    },
})
</script>


<template>
    <div class="flex justify-end sm:mr-2">
        <div 
            id="cart"
            class="fixed text-gray-900
            bg-gray-300 rounded-md flex flex-col
            p-4 top-[3.2rem] sm:w-[50%] lg:w-[30%] w-[100%] gap-2 max-h-[60vh]
        ">
            <h2 class="uppercase font-bold ">My Cart</h2>
            <hr>
            
            <div v-if="myCart.length < 1" class="text-gray-600 p-2 uppercase"><h2>Your cart is empty</h2></div>

            <div class="overflow-scroll overflow-x-hidden flex flex-col gap-2 no-scrollbar">
                <div class="transition-all duration-300 " v-for="(product, i) in myCart" :key="i">
                    <li class="flex gap-10 mx-5">
                        <img :src="product.image" alt="" width="64" class="rounded-md">
                        <div class="flex flex-col">
                            <p>{{ product.name }}</p>
                            <i class="text-green-700">KSH {{ product.price }}</i>                    
                            <button @click="removeFromCart(i)" 
                                class="relative bg-gray-900 hover:bg-red-700 
                                text-white px-[7px] rounded-full left-10 h-6
                                 w-10"
                            >
                                X
                            </button>
                        </div>
                    </li>
                </div>
            </div>
            <div v-if="myCart.length > 0">
                <hr>
                <div class="grid grid-cols-3">
                    <h3>Total</h3>
                    <i class="text-red-700">KSH 0</i>
                    <p>{{ myCart.length }} in cart</p>
                </div>
                <div class="flex justify-center">
                    <button class="bg-green-700 text-white p-2
                        rounded-md hover:bg-green-600
                        col-start-1 col-end-3
                        transition-all duration-300
                    ">
                        Checkout
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>

<style>
#cart {
    /* transform: translateX(60vw); */
    z-index: 12;
}
</style>