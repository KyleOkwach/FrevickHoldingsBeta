<script>
import Navbar from './components/Navbar.vue'
import Hero from './components/Hero.vue'
import Searchbar from './components/Searchbar.vue'
import Footer from './components/Footer.vue'
import { ref, computed, onMounted } from 'vue'

export default {
  name: 'App',
  components: {
    Navbar,
    Hero,
    Searchbar,
    Footer
  }
};
</script>

<script setup>
const query = ref('')
const cart = ref([])
const search_results = ref([])
const display_items = ref([])
const url = `src/api/items.json`

var isSearching = false // is the user searching

const searchItem = () => {
  fetch(url)
    .then(res => res.json())
    .then(data => search_results.value = data)

  isSearching = true
}

fetch(url)
  .then(res => res.json())
  .then(data => display_items.value = data)

const handleInput = e => {
  if (!e.target.value) {
    search_results.value = []
  }
}

</script>

<template>
  <!-- NAVBAR -->
  <div id="top"></div>

  <Navbar />

  <Hero />

  <Searchbar />

  <br />

  <div id="main">

    <!-- DISPLAY -->
    <h2 v-if="!isSearching" class="uppercase font-bold underline">Items of the day</h2>
    <div v-if="!isSearching"
      class="display 
      grid grid-flow-cols grid-cols-3
      gap-2 p-1"
    >
      <div v-for="(item, i) in display_items" :key="i"
        class="card rounded-md 
        text-left "
        
      >
        <div class="ovrflow-hidden">
          <li class="card-content m-4 relative">
            <img :src="item.image" class="object-contain" />
            <h3 class="">{{ item.name }}</h3>
            <i class="text-green-600"><p>KSH {{ item.price }}</p></i>
            <button class="bg-gray-700 p-2 rounded-md hover:bg-green-700 text-white transition-all duration 500"> Add to cart <i class="fa-solid fa-cart-plus"></i></button>
            <!-- <font-awesome-icon icon="fa-solid fa-heart" /> -->
          </li>
        </div>
      </div>

    </div>

    <!-- SEARCH -->
    <div v-if="isSearching"
      class="results
      grid grid-flow-cols grid-cols-3"
    >
      <div v-for="(item, i) in search_results" :key="i"
        class="card"
      >
        <img :src="item.image" width="64" height="64" />
        <div class="details">
          <h3>{{ item.name }}</h3>
        </div>
      </div>
    </div>

  </div>

  <Footer />

</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #1f1f1f;
}
.card {
	/*max-width: 15rem;*/
	box-shadow: 0px 0.5px 5px var(--bg-secondary);
	/*border-radius: 5px;*/
	padding: 10rem 0 0;
	overflow: hidden;
}

</style>
