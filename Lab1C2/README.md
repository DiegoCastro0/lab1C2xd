# Lab1C2

This template should help get you started developing with Vue 3 in Vite.

## Recommended IDE Setup

[VS Code](https://code.visualstudio.com/) + [Vue (Official)](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur).

## Recommended Browser Setup

- Chromium-based browsers (Chrome, Edge, Brave, etc.):
  - [Vue.js devtools](https://chromewebstore.google.com/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd)
  - [Turn on Custom Object Formatter in Chrome DevTools](http://bit.ly/object-formatters)
- Firefox:
  - [Vue.js devtools](https://addons.mozilla.org/en-US/firefox/addon/vue-js-devtools/)
  - [Turn on Custom Object Formatter in Firefox DevTools](https://fxdx.dev/firefox-devtools-custom-object-formatters/)

## Customize configuration

See [Vite Configuration Reference](https://vite.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```

Problematica:
En la comunidad gamer de San Miguel, El Salvador, muchos jugadores enfrentan dificultades para organizar torneos locales de videojuegos (como FIFA, Call of Duty, Free Fire o League of Legends). Actualmente, la coordinación se realiza de manera informal a través de grupos de redes sociales o mensajes privados, lo que genera problemas como:

Falta de información clara sobre fechas, reglas y premios.

Dificultad para inscribirse y confirmar participación.

Escasa visibilidad de los torneos para atraer nuevos jugadores o público.

Ausencia de un sistema de resultados y estadísticas en línea.

Esto limita el crecimiento de la comunidad gamer y reduce las oportunidades de interacción y competencia organizada.

preguntas:

- Explique con sus propias palabras qué es Vue.js y cuál es su función dentro de la
página web desarrollada.
R// en este caso vue.js es un framework bastante interesante que nos ayuda a estructurar nuestra web y nos da opciones bastante interesantes
por ejemplo el crear components y hacer ciertas funciones directamente en el template como por ejemplo en el v-if

- Describa qué variables reactivas utilizó en su aplicación y cuál es la función de
cada una dentro del sistema.
R// tenemos 5 que corresponden a espacios del formulario como nombre del torneo, juego, fecha, precio y cupos con los cuales guardamos esos datos y se muestran en una carta en el otro component

- Explique la diferencia entre las siguientes directivas utilizadas en su proyecto: v-
bind y v-model
R// v-model es para poner un valor en un atributo html y v-model es para conectar un input con una variable de manera que cambian juntos

- Mencione al menos un ejemplo de evento utilizado dentro de su aplicación.
R// En componente1.vue se usa @submit.prevent="addTournament" en el <form> y en componente2.vue se usa @click="emit('inscribir', t.id)" en un botón.

- Explique para qué utilizó la directiva v-for dentro de su aplicación.
Se usa en componente2.vue para recorrer la lista torneos y generar cada tarjeta de torneo: <li v-for="t in torneos" :key="t.id">.
Esto hace render dinámico de cada torneo en la lista.

- Describa en qué situación utilizó v-if y qué problema resuelve dentro de su
interfaz.
R//En componente2.vue: <p v-if="torneos.length === 0">No hay torneos aún.</p>. Resuelve el problema de mostrar un mensaje cuando no hay datos, evitando renderizar la lista vacía.

- Explique cómo se realiza la validación de datos en su aplicación y por qué es
importante validar la información ingresada por el usuario.
R// En componente1.vue, la validación está en canSubmit (longitud mínima de nombre y premio, fecha presente, slots entre 4 y 64). En addTournament(), si no canSubmit, se pone error y no emite. Esto previene datos incompletos/incorrectos y evita torneos inválidos en la UI.
