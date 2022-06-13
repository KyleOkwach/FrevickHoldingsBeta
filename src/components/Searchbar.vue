<script>
import { ref } from 'vue'
export default{
    name: 'Searchbar'
}
</script>
<template>
    <form @submit.prevent="searchItem" class="p-4">
        <input type="text" placeholder="search for item..." v-model="query" @input="handleInput" 
        class="h-8 border-[0.5px] border-slate-700 w-[30%]
        rounded-tl-md rounded-bl-md"
        />
        <button type="submit"
        class="bg-green-700 text-white h-8 w-20
        hover:bg-green-800 transition-all duration-500
        rounded-br-md rounded-tr-md"
        >Search</button>
    </form>
</template>