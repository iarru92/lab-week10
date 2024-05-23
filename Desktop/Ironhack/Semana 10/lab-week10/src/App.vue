<template>
  <div class="container">
    <div id="app" class="content">
      <Navbar />
      <router-view />
      <Footer />
      <div class="section">
        <h2>Resultado de la Operación Matemática</h2>
        <p class="result">{{ resultadoOperacion }}</p>
        <h2>Mensaje Personalizado</h2>
        <p class="message">{{ obtenerMensaje() }}</p>
      </div>
    </div>
    <div class="sidebar">
      <h2>Opciones</h2>
      <p v-if="mostrarElemento">
        Este elemento se mostrará si mostrarElemento es true.
      </p>
      <button @click="toggleMostrarElemento">Alternar Mostrar Elemento</button>
      <div :class="{ 'elemento-activo': fondoActivo }">
      </div>
      <button @click="toggleFondo">Cambiar Color de Fondo</button>
    </div>
    <div class="publicaciones">
      <h2>Lista de Publicaciones</h2>
      <div
        v-for="publicacion in publicaciones"
        :key="publicacion.id"
        class="publicacion"
      >
        <h3>{{ publicacion.titulo }}</h3>
        <p><strong>Descripción:</strong> {{ publicacion.descripcion }}</p>
        <p><strong>Contenido:</strong> {{ publicacion.contenido }}</p>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import Navbar from "./components/Navbar.vue";
import Footer from "./components/Footer.vue";

const publicaciones = ref([
  {
    id: 1,
    titulo: "Publicación 1",
    descripcion: "Descripción de la publicación 1",
    contenido: "Contenido de la publicación 1",
  },
  {
    id: 2,
    titulo: "Publicación 2",
    descripcion: "Descripción de la publicación 2",
    contenido: "Contenido de la publicación 2",
  },
  {
    id: 3,
    titulo: "Publicación 3",
    descripcion: "Descripción de la publicación 3",
    contenido: "Contenido de la publicación 3",
  },
]);

const resultadoOperacion = ref(2 + 2);

const dato1 = ref(5);
const dato2 = ref(3);

const obtenerMensaje = () => {
  return `El valor de dato1 es ${dato1.value} y el valor de dato2 es ${dato2.value}.`;
};

const mostrarElemento = ref(false);
o
const toggleMostrarElemento = () => {
  mostrarElemento.value = !mostrarElemento.value;
};

const fondoActivo = ref(false);

const toggleFondo = () => {
  fondoActivo.value = !fondoActivo.value;
};
</script>

<style scoped>
.container {
  display: flex;
}

.content {
  flex: 2;
  padding: 20px;
}

.section {
  margin-bottom: 40px;
}

.result {
  font-size: 24px;
  color: #333;
}

.message {
  font-style: italic;
  color: #666;
}

.sidebar {
  flex: 1;
  padding: 20px;
  background-color: #f4f4f4;
}

.publicaciones {
  flex: 3;
  padding: 20px;
}

.publicacion {
  margin-bottom: 20px;
  padding: 10px;
  background-color: #f9f9f9;
  border-radius: 5px;
}

.publicacion h3 {
  margin-top: 0;
}

button {
  background-color: #007bff;
  color: #fff;
  border: none;
  padding: 10px 20px;
  border-radius: 5px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}

.elemento-activo {
  background-color: lightblue;
}
</style>
