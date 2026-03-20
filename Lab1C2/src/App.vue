<script setup>
import { ref } from 'vue';
import Componente1 from './components/componente1.vue';
import Componente2 from './components/componente2.vue';

const torneos = ref([]);

function createTournament(torneo) {
  torneos.value.push(torneo);
}

function inscribir(id) {
  const t = torneos.value.find(x => x.id === id);
  if (t && t.participants < t.slots) t.participants++;
}

function setResult(id) {
  const t = torneos.value.find(x => x.id === id);
  if (t) t.results = 'Finalizado';
}

function deleteTournament(id) {
  torneos.value = torneos.value.filter(x => x.id !== id);
}

function clearAll() {
  torneos.value = [];
}
</script>

<template>
  <h1>Gestión de Torneos </h1>

  <Componente1 @create-tournament="createTournament" />

  <Componente2
    :torneos="torneos"
    @inscribir="inscribir"
    @set-result="setResult"
    @delete-tournament="deleteTournament"
    @clear-all="clearAll"
  />
</template>
