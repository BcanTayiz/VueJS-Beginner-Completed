

<template>
  <main>
    <div>
      <h4>The Current count is ...</h4>
      <h1>{{ count }}</h1>
      <button @click="subCount()">-</button>
      <button @click="addCount()">+</button>
    </div>
  </main>
</template>

<script setup>
import { ref } from 'vue';
const count = ref(0)
const addCount = () => {
  count.value += 1
}
const subCount = () => {
  count.value -= 1
}

</script>

<style scoped>
 main{
  background-color: aliceblue;
  width: 100vw;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
 }
 div{
  text-align: center;
 }
</style>
