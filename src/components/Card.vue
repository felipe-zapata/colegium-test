<script setup>

const props = defineProps({
  id: Number,
  alumnos_id: Number,
  asistencia: String,
  nombre: String,
  apellido: String,
  image: {
    type: String,
    default: 'https://placehold.co/400'
  },
})

</script>

<template>
  <article class="card">
    <img :src=image alt="profile image" class="card-image">
    <div class="card-name">{{ nombre }} {{ apellido }}</div>
    <div class="card-assist">
      <div class="card-circle" :class="{'card-circle_present': asistencia === 'presente'}">P</div>
      <div class="card-circle" :class="{'card-circle_ausent': asistencia === 'ausente'}">A</div>
      <div class="card-circle" :class="{'card-circle_late': asistencia === 'tarde'}">L</div>
    </div>
  </article>
</template>

<style scoped>
  .card {
    background-color: #fff;
    border-radius: 10px;
    border: 1px solid #e5e5e5;
    box-shadow: 1px 1px 1px rgba(0, 0, 0, 0.1);
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 20px;
    width: 25%;
    max-width: 200px;
    margin: 20px;
  }

  .card-image {
    width: 60px;
    height: auto;
    border-radius: 100%;
  }

  .card-name {
    font-weight: bold;
    margin-top: 1rem;
    margin-bottom: 1rem;
  }

  .card-assist {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    width: 70%;
  }
  
  .card-circle {
    border-radius: 100%;
    background-color: #F6F6FE;
    width: 2rem;
    height: 2rem;
    text-align: center;
    line-height: 2rem;
    border: 1px solid #bbbbbb;
  }

  .card-circle_present{
    color: #fff;
    background-color: #31CC93;
  }

  .card-circle_ausent{
    color: #fff;
    background-color: #EA4064;
  }

  .card-circle_late{
    color: #fff;
    background-color: #F8A148;
  }
</style>
