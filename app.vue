<template>
  <div class="container">
    <h1>bbnm</h1>
    <div class="options">
      <div class="option">
        <h4>1) Gender</h4>
        <div class="buttons">
          <button>Boy</button>
          <button>Unisex</button>
          <button>Girl</button>
        </div>
      </div>
      <div class="option">
        <h4>2) Popularity</h4>
        <div class="buttons">
          <button>Trendy</button>
          <button>Unique</button>
        </div>
      </div>
      <div class="option">
        <h4>3) Length</h4>
        <div class="buttons">
          <button>All</button>
          <button>Long</button>
          <button>Short</button>
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
}
button:first-of-type {
  border-top-left-radius: 4px;
  border-bottom-left-radius: 4px;
}
button:last-of-type {
  border-top-right-radius: 4px;
  border-bottom-right-radius: 4px;
}
</style>
