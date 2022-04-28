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
</script>

<template>
  <div class="container">
    <h1>bbnm</h1>
    <div class="options">

      <div class="option">
        <h4>1) Gender</h4>
        <div class="buttons">
          <button :class="{active: options.gender==Gender.BOY}" 
            @click="options.gender=Gender.BOY">Boy
          </button>
          <button :class="{active: options.gender==Gender.UNISEX}" 
            @click="options.gender=Gender.UNISEX">Unisex
          </button>
          <button :class="{active: options.gender==Gender.GIRL}"
            @click="options.gender=Gender.GIRL">Girl
          </button>
        </div>
      </div>

      <div class="option">
        <h4>2) Popularity</h4>
        <div class="buttons">
          <button :class="{active: options.popularity==Popularity.TRENDY}" 
            @click="options.popularity=Popularity.TRENDY">Trendy
          </button>
          <button :class="{active: options.popularity==Popularity.UNIQUE}"
            @click="options.popularity=Popularity.UNIQUE">Unique
          </button>
        </div>
      </div>

      <div class="option">
        <h4>3) Length</h4>
        <div class="buttons">
          <button :class="{active: options.length==Length.ALL}" 
            @click="options.length=Length.ALL">All
          </button>
          <button :class="{active: options.length==Length.LONG}" 
            @click="options.length=Length.LONG">Long
          </button>
          <button :class="{active: options.length==Length.SHORT}" 
            @click="options.length=Length.SHORT">Short
          </button>
        </div>
      </div>

      <button class="primary" @click="findNames">Find names</button>
    </div>
    
    <div class="cards">
      <div class="card" v-for="name in selectedNames">{{name}}</div>
    </div>
  </div>
</template>

<style scoped>
.container {
  font-family: Arial, Helveticam sans-serif;
}
.options, .cards {
  max-width: 330px;
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

.buttons {
  min-width: 240px;
  display: flex;
}

button {
  background-color: white;
  padding: 0.5rem;
  flex-grow: 1;
  border: none;
  margin: 0 1px;
  cursor: pointer;
}
button:first-of-type {
  border-top-left-radius: 4px;
  border-bottom-left-radius: 4px;
}
button:last-of-type {
  border-top-right-radius: 4px;
  border-bottom-right-radius: 4px;
}
button.active, button.primary {
  background-color: #fb9b9b;
  color: white;
}

button.primary {
  margin-top: 2rem;
}

.cards {
  margin-top: 1rem;
  display: flex;
  flex-wrap: wrap;
}
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
