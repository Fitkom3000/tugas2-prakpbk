<template>
  <div class="container">
    <div class="window" @click="stackBook" v-if="!canSeeOutside">
      <button class="book" v-for="(book, index) in books" :key="index" @click="stackBook"></button>
      <div class="person" :style="{ bottom: books.length * 20 + 'px' }"></div>
    </div>
    <p v-if="canSeeOutside">Moral Pendidikan: Belajar adalah kunci keberhasilan.</p>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const books = ref([])
const canSeeOutside = ref(false)

function stackBook() {
  if (!canSeeOutside.value) {
    books.value.push({})
    if (books.value.length >= 3) {
      canSeeOutside.value = true
    }
  }
}
</script>

<style>
.container {
  position: relative;
  width: 400px;
  height: 600px;
  background-color: #f0f0f0;
  overflow: hidden;
}

.window {
  position: absolute;
  width: 300px;
  height: 400px;
  background-color: #fff;
  border: 2px solid #000;
  top: 100px;
  left: 50px;
}

.book {
  position: absolute;
  width: 60px;
  height: 80px;
  background-color: #ffcc00;
  border: 2px solid #000;
  cursor: pointer;
}

.person {
  position: absolute;
  width: 40px;
  height: 100px;
  background-color: #ff0000;
  bottom: 0;
}
</style>
