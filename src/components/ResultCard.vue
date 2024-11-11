// ResultCard.vue
<template>
  <div class="max-w-auto rounded-3xl bg-white shadow-xl shadow-indigo-400/20">
    <div class="flex">
      <!-- Score Circle -->
      <div
        class="bg-gradient-to-b from-[#6742ff] to-[#332ceb] rounded-2xl p-9 text-center text-white flex flex-col items-center justify-center max-w-[300px] w-full"
      >
        <h2 class="text-xl mb-4 font-bold">Your Result</h2>
        <div
          class="rounded-full bg-gradient-to-b from-[#4b23ca] to-[#4633ed] w-[150px] h-[150px] flex flex-col items-center justify-center"
        >
          <span class="text-6xl font-bold">{{ averageScore }}</span>
          <span class="text-gray-300">of 100</span>
        </div>
        <h3 class="text-2xl mt-6 mb-2">Great</h3>
        <p class="text-gray-300">
          You scored higher than 65% of the people who have taken these tests.
        </p>
      </div>

      <!-- Summary Section -->
      <div class="flex-1 p-8">
        <h3 class="text-xl font-bold mb-6">Summary</h3>
        <div class="space-y-2">
          <ScoreItem
            v-for="item in scores"
            :key="item.category"
            :category="item.category"
            :score="item.score"
          />
        </div>
        <button
          class="w-full bg-indigo-600 text-white rounded-full py-3 mt-8 hover:bg-indigo-700 transition-colors"
        >
          Continue
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from "vue";
import ScoreItem from "./ScoreItem.vue";

const scores = ref([
  {
    category: "Reaction",
    score: 80,
    icon: "./src/assets/images/icon-reaction.svg",
  },
  {
    category: "Memory",
    score: 92,
    icon: "./src/assets/images/icon-memory.svg",
  },
  {
    category: "Verbal",
    score: 61,
    icon: "./src/assets/images/icon-verbal.svg",
  },
  {
    category: "Visual",
    score: 72,
    icon: "./src/assets/images/icon-visual.svg",
  },
]);

const averageScore = computed(() => {
  const totalScore = scores.value.reduce((sum, item) => sum + item.score, 0);
  return Math.round(totalScore / scores.value.length);
});
</script>
