## 🎨 Estética & Diseño
El proyecto utiliza una paleta de colores **High Contrast** basada en los gustos personales de la autora:
* **Rosa Pastel (#ffb7d5):** Utilizado en sombras sólidas y estados de interacción, aportando suavidad.
* **Negro (#1a1a1a):** Define los bordes gruesos y la tipografía, dando una estructura neobrutalista.
* **Mostaza (#ffdb58):** Color de acento para los botones de acción principal.
* **Celeste Pastel (#f0faff):** Color de fondo para una visualización descansada.



## 🚀 Funcionalidades Clave
-   **Binding Bidireccional:** Uso de `v-model` para la sincronización perfecta entre el input y el estado.
-   **Persistencia con LocalStorage:** Integración de un `watcher` profundo que guarda la lista automáticamente.
-   **Manejo de Eventos Avanzado:**
    -   `@submit.prevent`: Control total del envío del formulario.
    -   `@keyup.enter`: Experiencia de usuario fluida al añadir tareas.
    -   `@click.once`: Ejecución de lógica de inicialización única.
    -   `Ctrl + Enter`: Atajo de teclado personalizado para feedback de progreso.
-   **Animaciones Dinámicas:** Uso de `<TransitionGroup>` para transiciones suaves al gestionar tareas.

## 🛠️ Tecnologías Utilizadas
* [Vue.js 3](https://vuejs.org/) (Composition API)
* [Vite](https://vitejs.dev/) (Build Tool de nueva generación)
* [JavaScript](https://developer.mozilla.org/es/docs/Web/JavaScript) (ES6+)
* [CSS3](https://developer.mozilla.org/es/docs/Web/CSS) (Flexbox y animaciones)

## 📦 Instalación y Uso

1. Clona este repositorio:
   ```bash
   git clone [https://github.com/Traipe/vue-todo-app.git](https://github.com/Traipe/vue-todo-app.git)

2. Entra a la carpeta del proyecto:

cd vue-todo-app

3. Instala las dependencias:

npm install

4.  Inicia el servidor de desarrollo:

npm run dev


Creado por [Traipe] (©) como parte de mi camino hacia Front-end Trainee.

|
*Este trabajo pertenece al M6 DESARROLLO DE INTERFACES INTERACTIVAS CON FRAMEWORK VUE