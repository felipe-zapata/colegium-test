<script setup>
import Card from './Card.vue'
import axios from "axios";
import { onMounted, ref } from 'vue'

const cardList = ref([])

async function getData() {
  try {
    const asistencias = await axios.get('https://x8ki-letl-twmt.n7.xano.io/api:Yg52T3Tp/asistencias')
    const alumnos = await axios.get('https://x8ki-letl-twmt.n7.xano.io/api:Yg52T3Tp/alumnos')
    cardList.value = asistencias?.data?.map((asistencia) => {
      const alumno = alumnos?.data?.find((alumno) => alumno.id === asistencia.alumnos_id)
      return {
        ...asistencia,
        nombre: alumno?.nombre ?? 'Sin nombre',
        apellido: alumno.Apellido ?? 'Sin apellido'
      }
    })
  } catch (error) {
    console.error(error)
  }
}

onMounted(() => {
  getData()
})

</script>

<template>
  <section class="cardSection">
      <Card v-for="alumno in cardList" v-bind="alumno" />
  </section>
</template>

<style scoped>
  .cardSection {
    display: flex;
    flex-direction: row;
    justify-content: flex-start;
    flex-wrap: wrap;
  }
</style>
