<script>
import { ref } from 'vue'
export default{
    name: 'Searchbar',
    props: {
        val: ''
    }
}
</script>
<template>
    <form @submit.prevent="searchItem" class="p-4">
        <input type="text" placeholder="search for item..." v-model="val" @input="handleInput" 
        class="h-8 border-[0.5px] border-slate-700 sm:w-[30%] w-[60%]
        rounded-tl-md rounded-bl-md"
        />
        <button type="submit"
        class="bg-green-700 text-white h-8 w-20
        hover:bg-green-800 transition-all duration-500
        rounded-br-md rounded-tr-md"
        >Search</button>
    </form>
</template>