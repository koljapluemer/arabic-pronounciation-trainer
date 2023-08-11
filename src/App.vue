<script setup>
import words from "./words.js";
import { ref } from "vue";

let randomWord = ref([]);

function getRandomWord() {
  isRevealed.value = false;
  randomWord.value = words[Math.floor(Math.random() * words.length)];
}

let isRevealed = ref(false);

getRandomWord();
</script>

<template>

  <div class="card bg-base-300 shadow-xl m-4 flex flex-col items-center w-full max-w-screen-sm">
    <div class="card-body">
      <h2 class="card-title  my-2 text-6xl">{{ randomWord[0] }}</h2>
      <p :class="{'hidden': !isRevealed}" class="my-2 text-4xl">
      
      {{ randomWord[1] }}</p>
      <div class="card-actions justify-end mt-6">
        <button class="btn btn-primary" @click="isRevealed=true" v-if="!isRevealed">
          I have copied and tried to pronounce the word
        </button>
        <button class="btn btn-primary" @click="getRandomWord" v-else>
          New Random Word
        </button>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
