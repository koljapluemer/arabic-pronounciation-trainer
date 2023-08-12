<script setup>
import words from "./words.js";
import { ref } from "vue";

let randomWord = ref([]);

function getRandomWord() {
  isRevealed.value = false;
  const newWord = words[Math.floor(Math.random() * words.length)];
  
  randomWord.value = newWord;
}

let isRevealed = ref(false);

getRandomWord();
</script>

<template>
  <div
    class="card bg-base-300 shadow-xl m-4 flex flex-col items-center w-full max-w-screen-sm"
  >
    <div class="card-body">
      <h2 class="card-title my-2 text-6xl">{{ randomWord.og }}</h2>
      <div :class="{ hidden: !isRevealed }" class="flex items-center gap-2">
        <p class="my-2 text-4xl">
          {{ randomWord.translit }}
        </p>
        <a :href="`https://forvo.com/search/${randomWord.og}/ar/`" target="_blank">
          <svg
            aria-hidden="true"
            fill="none"
            stroke="currentColor"
            stroke-width="1.5"
            viewBox="0 0 24 24"
            xmlns="http://www.w3.org/2000/svg"
            class="w-6 h-6"
          >
            <path
              d="M19.114 5.636a9 9 0 010 12.728M16.463 8.288a5.25 5.25 0 010 7.424M6.75 8.25l4.72-4.72a.75.75 0 011.28.53v15.88a.75.75 0 01-1.28.53l-4.72-4.72H4.51c-.88 0-1.704-.507-1.938-1.354A9.01 9.01 0 012.25 12c0-.83.112-1.633.322-2.396C2.806 8.756 3.63 8.25 4.51 8.25H6.75z"
              stroke-linecap="round"
              stroke-linejoin="round"
            ></path>
          </svg>
        </a>
      </div>
      <div class="card-actions justify-end mt-6">
        <button
          class="btn btn-primary"
          @click="isRevealed = true"
          v-if="!isRevealed"
        >
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
