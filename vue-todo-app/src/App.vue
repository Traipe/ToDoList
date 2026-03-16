<script setup>
import { ref, watch, onMounted } from 'vue';

// --- ESTADO ---
const nuevaTarea = ref('');
const tareas = ref(JSON.parse(localStorage.getItem('mis-tareas')) || []);

// --- PERSISTENCIA (LocalStorage) ---
watch(tareas, (val) => {
  localStorage.setItem('mis-tareas', JSON.stringify(val));
}, { deep: true });

// --- MÉTODOS ---
const agregarTarea = () => {
  if (!nuevaTarea.value.trim()) return;
  tareas.value.push({
    id: Date.now(),
    texto: nuevaTarea.value,
    completada: false
  });
  nuevaTarea.value = '';
};

const eliminarTarea = (id) => {
  tareas.value = tareas.value.filter(t => t.id !== id);
};

// Acción .once
const avisoCarga = () => console.log("¡Primera interacción detectada!");

// Plus: Ctrl + Enter
const felicitacion = () => {
  const completadas = tareas.value.filter(t => t.completada).length;
  if (completadas >= 3) alert("¡Gud Work Chica! ¡Sigue así! 🚀");
};
</script>

<template>
  <main class="container">
    <h1>📝 My Todo List para mis tareas</h1>

   <form @submit.prevent="agregarTarea" class="input-group">
  <input 
    v-model="nuevaTarea" 
    @keyup.enter="agregarTarea"
    @keydown.control.enter="felicitacion"
    placeholder="¿Qué planes tienes hoy?"
  >
  <button @click.once="avisoCarga">Añadir</button>
</form>

    <TransitionGroup name="list" tag="ul">
      <li v-for="tarea in tareas" :key="tarea.id" class="todo-item">
        <span class="texto-tarea" :class="{ done: tarea.completada }" @click="tarea.completada = !tarea.completada">
          {{ tarea.texto }}
        </span>
        <button @click="eliminarTarea(tarea.id)" class="delete-btn">×</button>
      </li>
    </TransitionGroup>
  </main>
</template>

<style>
/*estilooo*/
/* Reset básico */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background-color: #f0faff;
  /* Celeste pastel muy suave de fondo */
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  color: #1a1a1a;
  /* Negro casi puro */
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
}

.container {
  max-width: 450px;
  width: 90%;
  background: #ffffff;
  padding: 2.5rem;
  border-radius: 20px;
  box-shadow: 10px 10px 0px #ffb7d5;
  /* Sombra sólida Rosa Pastel */
  border: 3px solid #1a1a1a;
  /* Borde Negro */
}

h1 {
  text-align: center;
  color: #1a1a1a;
  margin-bottom: 1.5rem;
  font-size: 1.8rem;
  text-transform: uppercase;
  letter-spacing: 2px;
}

/* El input y el grupo */
.input-group {
  display: flex;
  gap: 10px;
  margin-bottom: 2rem;
}

input {
  flex: 1;
  padding: 12px;
  border: 2px solid #1a1a1a;
  border-radius: 8px;
  outline: none;
  font-size: 1rem;
}

input:focus {
  background-color: #e3f2fd;
  /* Celeste pastel al escribir */
}

button {
  background-color: #ffdb58;
  /* Mostaza */
  color: #1a1a1a;
  border: 2px solid #1a1a1a;
  padding: 10px 20px;
  border-radius: 8px;
  font-weight: bold;
  cursor: pointer;
  transition: transform 0.2s;
}

button:hover {
  transform: translateY(-3px);
  background-color: #f4ca16;
  /* Mostaza más intenso */
}

/* Lista de tareas */
.todo-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 12px;
  margin-bottom: 10px;
  background: #ffffff;
  border: 2px solid #1a1a1a;
  border-radius: 10px;
  transition: all 0.3s;
}

.todo-item:hover {
  border-color: #ffb7d5;
  /* Cambia a Rosa Pastel al pasar el mouse */
}

.done {
  text-decoration: line-through;
  color: #a0a0a0;
  opacity: 0.6;
}

.texto-tarea {
  cursor: pointer;
  font-weight: 500;
  flex: 1;
}

.delete-btn {
  /* Rosa Pastel */
  color: #1a1a1a;
  border: 1.5px solid #1a1a1a;
  width: 30px;
  height: 30px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
  padding: 0;
  font-size: 1.2rem;
}
.delete-btn:hover {
  background: #ff85b3; /* Un rosa un poco más fuerte al pasar el mouse */
  box-shadow: 0 0 10px #ffb7d5;
  transform: scale(1.1);
}
/* Animaciones */
.list-enter-active,
.list-leave-active {
  transition: all 0.4s cubic-bezier(0.5, 0, 0.5, 1);
}

.list-enter-from {
  opacity: 0;
  transform: scale(0.8);
}

.list-leave-to {
  opacity: 0;
  transform: translateX(50px);
}
</style>