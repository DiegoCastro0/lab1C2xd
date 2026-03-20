<script setup>
const props = defineProps({
  torneos: { type: Array, default: () => [] }
});
const emit = defineEmits(['inscribir', 'set-result', 'delete-tournament', 'clear-all']);
</script>

<template>
  <section class="card">
    <div class="header-row">
      <h2>Torneos Activos</h2>
      <button class="small" @click="emit('clear-all')">Limpiar todo</button>
    </div>

    <p v-if="torneos.length === 0" class="empty">No hay torneos aún. Crea el primero.</p>

    <ul v-else class="tournament-list">
      <li v-for="t in torneos" :key="t.id">
        <h3>{{ t.name }} <small>({{ t.game }})</small></h3>
        <p>{{ t.date }} • {{ t.prize }} • Cupos: {{ t.slots }}</p>
        <p>Inscritos: {{ t.participants }} • Resultado:
          <span :class="t.results === 'Pendiente' ? 'pending' : 'done'">{{ t.results }}</span>
        </p>
        <div class="actions">
          <button @click="emit('inscribir', t.id)">Inscribir</button>
          <button @click="emit('set-result', t.id)">Marcar resultado</button>
          <button @click="emit('delete-tournament', t.id)">Eliminar</button>
        </div>
      </li>
    </ul>
  </section>
</template>

<style scoped>
.card {
  background:#20232a;
  border:2px solid #27ae60;
  border-radius:12px;
  padding:16px;
  margin-bottom:16px;
  color:#fff;
}
.header-row { display:flex; justify-content:space-between; align-items:center; }
.small {
  background:#e74c3c; color:#fff;
  border:none; border-radius:6px;
  padding:6px 10px; cursor:pointer;
}
.empty { font-style:italic; color:#aaa; }
.tournament-list { list-style:none; padding-left:0; }
.tournament-list li {
  border-top:1px solid #444;
  padding-top:10px; margin-top:10px;
}
.actions button {
  margin-right:6px; margin-top:8px;
  border:none; border-radius:6px;
  padding:6px 10px; background:#2f80ed;
  color:#fff; cursor:pointer; font-weight:bold;
}
.pending { color:#f39c12; }
.done { color:#27ae60; }
</style>
