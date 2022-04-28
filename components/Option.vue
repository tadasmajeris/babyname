<script setup lang="ts">
import { Gender, Popularity, Length } from "@/data"

interface Props {
  option: {
    title: string;
    category: string;
    buttons: Gender[] | Popularity[] | Length[];
  },
  options: {
    gender: Gender;
    popularity: Popularity;
    length: Length;
  }
}

const props = defineProps<Props>()
</script>

<template>
  <div class="option">
    <h4>{{option.title}}</h4>
    <div class="buttons">
      <button 
        v-for="value in option.buttons" :key="value" 
        :class="{active: options[option.category]==value}" 
        @click="options[option.category]=value"
      >
        {{value}}
      </button>
    </div>
  </div>
</template>

<style scoped>
button:first-of-type {
  border-top-left-radius: 4px;
  border-bottom-left-radius: 4px;
}
button:last-of-type {
  border-top-right-radius: 4px;
  border-bottom-right-radius: 4px;
}
button.active {
  background-color: #fb9b9b;
  color: white;
}

.buttons {
  min-width: 240px;
  display: flex;
}
</style>