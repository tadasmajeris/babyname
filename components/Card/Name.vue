<script lang="ts" setup>
interface Props {
  name: string;
  index: number;
}
const props = defineProps<Props>()

const emit = defineEmits(["remove "])
const removeName = () => {
  emit("remove", props.index)
}
</script>

<template>
  <div class="card">
    <h4>{{name}}</h4>
    <div class="x" @click="removeName(name)">x</div>
  </div>
</template>

<style scoped>
.card {
  box-sizing: border-box;
  width: calc(50% - 2px);
  padding: 1rem;
  text-align: center;
  background: #ffd4d4;
  margin: 1px;
  border-radius: 4px;
  position: relative;
}

h4 {
  margin: 0;
}

.x {
  cursor: pointer;
  position: absolute;
  right: 7px;
  top: 2px;
  color: white;
}
</style>