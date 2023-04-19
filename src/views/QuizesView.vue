<script setup>
  import q from "../data/quizes.json"
  import {ref, watch} from "vue"
  import Card from "../components/Card.vue"

  const quizes = ref(q)
  const search = ref("")

  watch(search, () => {
    quizes.value = q.filter(quiz => quiz.name.toLowerCase().includes(search.value.toLowerCase()))
  })

</script>

<template>
    <div>
    <header>
      <h1>Quizes</h1>
      <input v-model.trim="search" type="text" placeholder="search...">
    </header>
    <div class="options-container">
      <Card v-for="quiz in quizes" :key="quiz.id" :quiz="quiz" /> 
    </div>
  </div>
</template>

<style scoped> 

  header {
    margin-bottom: 10px;
    margin-top: 30px;
    display: flex;
    align-items: center;
  }

  header h1 {
    font-style: bold;
    margin-right: 30px;
  }

  header input {
    border: none;
    padding: 10px;
    border-radius: 5px;
  }

  .options-container {
    display: flex;
    flex-wrap: wrap;
    margin-top: 40px;
  }
  
  /* CARD */

  .card {
    width: 310px;
    overflow: hidden;
    border-radius: 2%;
    box-shadow: 1px 1px 10px rgb(188, 241, 152);
    margin-bottom: 53px;
    margin-right: 20px;
    cursor: pointer; 
  }

  .card img {
    width: 100%;
    height: 190px;
    margin: 0;
  }

  .card .card-text {
    padding: 0 5px;
  }

  .card .card-text h2 {
    font-weight: bold;
  }
</style>