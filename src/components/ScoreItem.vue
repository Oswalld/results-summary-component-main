// ScoreItem.vue
<template>
  <div
    class="flex items-center justify-between p-4 rounded-xl min-w-[250px]"
    :class="backgroundClass"
  >
    <div class="flex items-center gap-2">
      <img :src="iconPath" :alt="category" class="w-5 h-5" />
      <span class="font-bold" :class="textClass">{{ category }}</span>
    </div>
    <div>
      <span class="font-bold">{{ score }}</span>
      <span class="text-gray-400"> / 100</span>
    </div>
  </div>
</template>

<script setup>
import { computed } from "vue";

const props = defineProps({
  category: {
    type: String,
    required: true,
  },
  score: {
    type: Number,
    required: true,
  },
});

const backgroundClass = computed(() => {
  const classes = {
    Reaction: "bg-red-50",
    Memory: "bg-yellow-50",
    Verbal: "bg-green-50",
    Visual: "bg-blue-50",
  };
  return classes[props.category];
});

const textClass = computed(() => {
  const classes = {
    Reaction: "text-red-500",
    Memory: "text-yellow-500",
    Verbal: "text-green-500",
    Visual: "text-blue-500",
  };
  return classes[props.category];
});

const iconPath = computed(() => {
  return `./src/assets/images/icon-${props.category.toLowerCase()}.svg`;
});
</script>
