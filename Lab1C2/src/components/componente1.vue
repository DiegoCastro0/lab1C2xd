<script setup>
import { ref, computed } from 'vue';
const emit = defineEmits(['create-tournament']);

const name = ref('');
const game = ref('FIFA');
const date = ref('');
const prize = ref('Trofeo + $50');
const slots = ref(8);
const error = ref('');

const games = ['FIFA', 'Call of Duty', 'Free Fire', 'League of Legends'];

const canSubmit = computed(() =>
  name.value.trim().length > 2 &&
  date.value &&
  prize.value.trim().length > 3 &&
  slots.value >= 4 && slots.value <= 64
);

function addTournament() {
  if (!canSubmit.value) {
    error.value = 'Completa todos los campos antes de crear el torneo.';
    return;
  }

  emit('create-tournament', {
    id: Date.now(),
    name: name.value.trim(),
    game: game.value,
    date: date.value,
    prize: prize.value.trim(),
    slots: slots.value,
    participants: 0,
    results: 'Pendiente'
  });

  // Reset
  name.value = '';
  game.value = 'FIFA';
  date.value = '';
  prize.value = 'Trofeo + $50';
  slots.value = 8;
  error.value = '';
}
</script>

<template>
  <section class="card">
    <h2>Crear Torneo</h2>
    <form @submit.prevent="addTournament">
      <label>Nombre</label>
      <input v-model="name" placeholder="Torneo San Miguel" />

      <label>Juego</label>
      <select v-model="game">
        <option v-for="g in games" :key="g">{{ g }}</option>
      </select>

      <label>Fecha</label>
      <input type="date" v-model="date" />

      <label>Premio(colocar $ primero y un minimo de $100)</label>
      <input v-model="prize" placeholder="$200 o trofeo" />

      <label>Cupos</label>
      <input type="number" min="4" max="64" v-model.number="slots" />

      <button type="submit" :disabled="!canSubmit">Crear torneo</button>
    </form>
    <p v-if="error" class="error">{{ error }}</p>
  </section>
</template>

<style scoped>
.card { background:#fff; border:1px solid #ddd; border-radius:12px; padding:14px; margin-bottom:12px; }
label { display:block; margin-top:10px; font-weight:600; }
input, select { width:100%; padding:6px; margin-top:4px; border-radius:6px; border:1px solid #bbb; }
button { margin-top:12px; padding:8px 12px; border-radius:8px; border:none; background:#2f80ed; color:white; cursor:pointer; }
button:disabled { opacity:.5; cursor:not-allowed; }
.error { color:#c0392b; margin-top:10px; }
</style>
