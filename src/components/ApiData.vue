<script setup>
import { ref, onMounted } from 'vue'
const quote = ref('');
const character = ref('');
const anime = ref('');

const fetchQuote = async () => {
      try {
        const response = await fetch('https://animechan.xyz/api/random');
        const data = await response.json();
        quote.value = data.quote;
        character.value = data.character;
        anime.value = data.anime;
      } catch (error) {
        console.error('Error fetching data:', error);
      }
};
onMounted(fetchQuote);
</script>
<template>
<section class="max-w-[700px] mt-5 mb-20 mx-5 md:mx-auto shadow-lg shadow-slate-100 px-5 py-10 border rounded">
    <h2 class="text-center text-2xl font-bold mb-3">Retrieved JSON object data</h2>
    <span class="text-lg first-letter-large"> {{ quote }}</span>
    <h3 class="font-bold">Anime: <span class="font-normal">{{ anime }}</span></h3>
    <h3 class="font-bold">Character: <span class="font-normal">{{ character }}</span></h3>
</section>
</template>
<style scoped>

</style>