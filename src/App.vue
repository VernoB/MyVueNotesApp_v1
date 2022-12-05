<script setup>
import { ref } from 'vue';

const showModal =  ref(false);
const textModal = ref('');
const Notes = ref([]);

const getRandomColor = () => {
  return "hsl(" + Math.random() * 360 + ", 100%, 75%)";
}

const addNote = () => {
  Notes.value.push({
    id: Math.floor(Math.random() * 10000000),
    text: textModal.value,
    dateNote: new Date(),
    backgroundColor: getRandomColor()
  })
  showModal.value = false;
  textModal.value = '';
}

</script>

<template>
  <main>
    <div class="container">
      <div v-if="showModal" class="overlay">
        <div class="modal">
          <textarea v-model="textModal" name="note" id="note" cols="30" rows="10"></textarea>
          <button @click="addNote" >add notes</button>
          <button class="close" @click="showModal = !showModal">Close</button>
        </div>
      </div>
      <header>
        <h1>Notes</h1>
        <button @click="showModal = !showModal">+</button>
      </header>
      <div class="cards-container">
        <div v-for="{text, dateNote, backgroundColor} in Notes" class="card" :style="{backgroundColor:backgroundColor}">
          <p class="main-text">{{text}}</p>
          <p class="date">{{dateNote.toLocaleDateString("en-US")}}</p>
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
  max-height: 1000px;
  margin: 0 auto;
  padding: 10px;
}
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
header button {
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

.overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.77);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 2;
}

.modal {
  width: 750px;
  background-color: #ddd;
  border-radius: 10px;
  padding: 30px;
  position: relative;
  display: flex;
  flex-direction: column;
;
}

.modal button {  
  padding: 10px 20px;
  font-size: 20px;
  width: 100%;
  background-color: blueviolet;
  border: none;
  color: #ddd;
  cursor: pointer;
  margin-top: 15px;
}
.modal .close {
  background-color: rgb(138, 97, 97);
  margin-top: 7px;
}
</style>