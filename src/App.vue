<script setup>
import { ref } from 'vue';

const showModal =  ref(false);
const textModal = ref('');
const errorMessages = ref('');
const Notes = ref([]);

const getRandomColor = () => {
  return "hsl(" + Math.random() * 360 + ", 100%, 75%)";
}

const addNote = () => {
  if (textModal.value.length < 10) {
    return errorMessages.value = "Please enter a text with minimun of 10 length.";
  }

  Notes.value.push({
    id: Math.floor(Math.random() * 10000000),
    text: textModal.value,
    dateNote: new Date(),
    backgroundColor: getRandomColor()
  })
  showModal.value = false;
  textModal.value = '';
  errorMessages.value = '';
}

</script>

<template>
  <main>
    <div class="container">
      <div v-if="showModal" class="overlay">
        <div class="modal">
          <textarea v-model.trim="textModal" name="note" id="note" cols="30" rows="10"></textarea>
          <p v-if="errorMessages">{{errorMessages}}</p>
          <button @click="addNote" >add notes</button>
          <button class="close" @click="showModal = !showModal">Close</button>
        </div>
      </div>
      <header>
        <h1>Notes</h1>
        <button @click="showModal = !showModal">+</button>
      </header>
      <div class="cards-container">
        <div v-for="{id, text, dateNote, backgroundColor} in Notes" class="card" :style="{backgroundColor:backgroundColor}" :key="id">
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
  margin: 0 auto;
  padding: 10px;
}
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

h1 {
  font-weight: bold;
  margin-bottom: 25px;
  font-size: 75px;
}

header button {
  border: none;
  padding: 10px;
 width: 50px;
 height: 50px;
 background-color: rgba(21,20,20);
  color: #ddd;
  border-radius: 100%;
  font-size: 20px;
  cursor: pointer;
}


.card {
  width: 225px;
  height: 225px;
  padding: 10px;  
  border-radius: 15px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  margin-right: 20px;
  margin-bottom: 20px;
}

.date {
  font-size: 12px;
  font-weight: bold;
}

.cards-container {
  display: flex;
  flex-wrap: wrap;
}

.overlay {
  position: absolute;
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

.modal p {
  color: rgb(138, 97, 97);
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