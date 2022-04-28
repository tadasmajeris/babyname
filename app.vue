<script lang="ts" setup>
  enum Gender {
    GIRL = 'Girl',
    BOY = 'Boy',
    UNISEX = 'Unisex'
  } 
  
  enum Popularity {
    TRENDY = 'Trendy',
    UNIQUE = 'Unique',
  } 

  enum Length {
    SHORT = 'Short',
    LONG = 'Long',
  }

  interface OptionsState {
    gender: string;
    popularity: string;
    length: string;
  }

  const options = reactive<OptionsState>({
    gender: Gender.GIRL,
    popularity: Popularity.TRENDY,
    length: Length.SHORT
  });
</script>

<template>
  <div class="container">
    <h1>bbnm</h1>
    <div class="options">
      <div class="option">
        <h4>1) Gender</h4>
        <div class="buttons">
          <button :class="{active: options.gender==Gender.BOY}">Boy</button>
          <button :class="{active: options.gender==Gender.UNISEX}">Unisex</button>
          <button :class="{active: options.gender==Gender.GIRL}">Girl</button>
        </div>
      </div>
      <div class="option">
        <h4>2) Popularity</h4>
        <div class="buttons">
          <button :class="{active: options.popularity==Popularity.TRENDY}">Trendy</button>
          <button :class="{active: options.popularity==Popularity.UNIQUE}">Unique</button>
        </div>
      </div>
      <div class="option">
        <h4>3) Length</h4>
        <div class="buttons">
          <button :class="{active: options.length==Length.ALL}">All</button>
          <button :class="{active: options.length==Length.LONG}">Long</button>
          <button :class="{active: options.length==Length.SHORT}">Short</button>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.container {
  font-family: Arial, Helveticam sans-serif;
}

.options {
  background-color: #feeaea;
  padding: 1rem;
  border-radius: 0.5rem;
  max-width: 300px;
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
button.active {
  background-color: #fb9b9b;
  color: white;
}
</style>
