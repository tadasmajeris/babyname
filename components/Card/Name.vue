<script lang="ts" setup>
interface NameProps {
  name: string;
}
const props = defineProps<NameProps>()
</script>

<template>
  <div class="card">{{name}}</div>
</template>

<style scoped>
.card {
  box-sizing: border-box;
  width: calc(33.3% - 2px);
  padding: 1rem;
  text-align: center;
  background: #ffd4d4;
  margin: 1px;
  border-radius: 4px;
}
</style>