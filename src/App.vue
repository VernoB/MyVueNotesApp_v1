<template>
  <main>
    <div class="container">
      <header>
        <h1>Notes</h1>
        <button>+</button>
      </header>
      <div class="cards-container">
        <div class="card">
          <p class="main-text">Lorem ipsum dolor, sit amet consectetur adipisicing elit. Quidem est consequuntur quisquam, minus ullam mollitia molestiae dolorem similique.</p>
          <p class="date">04/12/5698</p>
        </div>
        <div class="card">
          <p class="main-text">Lorem ipsum dolor sit amet consectetur adipisicing elit. Consequatur.</p>
          <p class="date">04/12/5698</p>
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
  transform: scale(1);
}

h1 {
  font-weight: bold;
  margin-bottom: 25px;
  font-size: 75px;
}

.card {
  width: 225px;
  height: 225px;
  background-color: rgba(237, 191,191);
  padding: 10px;  
  border-radius: 15px;
  display: flex;
  justify-content: space-between;
  margin-right: 20px;
  margin-bottom: 20px;
  flex-direction: column;
}

.date {
  font-size: 12px;

}

.cards-container {
  display: flex;flex-wrap: wrap;
}
</style>