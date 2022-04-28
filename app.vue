<script lang="ts" setup>
  import {Gender, Popularity, Length, names} from './data'

  interface OptionsState {
    gender: string;
    popularity: string;
    length: string;
  }

  const options = reactive<OptionsState>({ // selected options
    gender: Gender.GIRL,
    popularity: Popularity.TRENDY,
    length: Length.SHORT
  });

  const selectedNames = ref<string[]>([])

  const findNames = () => {
    const filteredNames = names.filter(name => name.gender == options.gender)
                              .filter(name => name.popularity == options.popularity)
                              .filter(name => {
                                if (options.length === Length.ALL) return true
                                else return name.length === options.length
                              });
    selectedNames.value = filteredNames.map(n => n.name);
  }

  const optionsArray = [
    {
      title: '1) Gender',
      category: 'gender',
      buttons: [Gender.GIRL, Gender.UNISEX, Gender.BOY]
    },
    {
      title: '2) Popularity',
      category: 'popularity',
      buttons: [Popularity.TRENDY, Popularity.UNIQUE]
    },
    {
      title: '3) Length',
      category: 'length',
      buttons: [Length.ALL, Length.SHORT, Length.LONG]
    }
  ]

  const removeName = (index: number) => {
    const filteredNames = [...selectedNames.value]
    filteredNames.splice(index, 1);
    selectedNames.value = filteredNames;
  }
</script>

<template>
  <div class="container">
    <h1>bbnm</h1>
    <div class="options">
      <Option v-for="option in optionsArray" :key="option.title" :option="option" :options="options" />
      <button class="primary" @click="findNames">Find names</button>
    </div>
    
    <div class="cards">
      <CardName v-for="(name, i) in selectedNames" :key="i" :name="name" @remove="()=>removeName(i)" :index="i"/>
    </div>
  </div>
</template>

<style>
button {
  background-color: white;
  padding: 0.5rem;
  flex-grow: 1;
  border: none;
  margin: 0 1px;
  cursor: pointer;
}
</style>

<style scoped>
.container {
  font-family: Arial, Helveticam sans-serif;
}
.options, .cards {
  max-width: 320px;
}
.options {
  box-sizing: border-box;
  background-color: #feeaea;
  padding: 1rem;
  border-radius: 0.5rem;
  text-align: center;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding-bottom: 2.5rem;
}

button.primary {
  background-color: #fb9b9b;
  color: white;
  margin-top: 2rem;
  border-radius: 4px;
}

.cards {
  margin-top: 1rem;
  display: flex;
  flex-wrap: wrap;
}
</style>
// 150