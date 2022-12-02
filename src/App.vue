<template>
  <main>
    <div class="container">
      <header>
        <h1>Notes</h1>
        <button>+</button>
      </header>
      <div class="card-container">
        <div class="card">
          <p class="main"></p>
          <p class="date"></p>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
main {
  height: 100vh;
  width: 100vw;
}
.container {
  max-width: 1000px;
  margin: 0 auto;
  padding: 10px;
}
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
button {
 width: 50px;
 height: 50px;
 background-color: rgba(21,20,20);
  border: 1px solid #ddd;
  color: #ddd;
  border-radius: 50px;
  font-size: 20px;
  cursor: pointer;
}

button:hover {
  animation: ease;
  transform: scale(1deg);
}

h1 {
  font-weight: bold;
  margin-bottom: 25px;
  font-size: 75px;
}
</style>