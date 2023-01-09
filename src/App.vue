<template>
  <div id="app">
    <div id="app-3">
      <span v-if="seen">Ahora me ves</span>
    </div>
    <div id="app-5">
      <p>{{ message }}</p>
      <button v-on:click="reverseMessage">Mensaje invertido</button>
    </div>
    <div id="app-6">
      <p>{{ message }}</p>
      <input v-model="message">
    </div>
    <div>
      <br>
      {{ contenido }}
      <div>
        <input type="text" v-model="nuevoLenguaje" @keyup.enter="agregarLenguaje" />
        <input type="text" v-model="nuevoLink" @keyup.enter="agregarLenguaje" />
        <button @click="agregarLenguaje">Agregar lenguaje</button>
      </div>
      <ul>
        <li v-for="lenguaje of lenguajes" :key="lenguaje.nombre">
          <a :href="lenguaje.link" target="_blank">{{ lenguaje.nombre }}</a> {{ lenguaje.puntos }}
          <button @click="lenguaje.puntos++">+</button>
          <button @click="lenguaje.puntos--">-</button>
        </li>
      </ul>
      Suma de todos los votos {{ sumarTodo }}
      <br>
      <br>
      <br>
    </div>
    <div id="elemento" class="container mt-3">
      <div v-bind:class="['p-2', 'text-white', colorFondo]">
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Illum non doloribus iste veniam voluptatibus, sequi id
        quia maxime minima, saepe eveniet autem aut? Earum non quisquam ex repellendus hic nesciunt.
      </div>
      <input type="text" v-model="colorFondo">
      <br>
      <br>
      <div class="p-2 text-white" :class="{ 'bg-danger': cambioColor, 'bg-primary': !cambioColor }">
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Illum non doloribus iste veniam voluptatibus, sequi id
        quia maxime minima, saepe eveniet autem aut? Earum non quisquam ex repellendus hic nesciunt.
      </div>
      <button class="btn btn-primary" @click="cambioColor = !cambioColor">Cambia color</button>
      <div v-bind:class="classArray">
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Illum non doloribus iste veniam voluptatibus, sequi id
        quia maxime minima, saepe eveniet autem aut? Earum non quisquam ex repellendus hic nesciunt.
      </div>
    </div>
    <div id="elemento" class="container mt-5">
      <h3>{{ texto }}</h3>
      <h3>{{ alReves }}</h3>
      <input type="text" v-model="texto">
      <hr>
      <div class="progress">
        <div class="progress-bar" role="progressbar" aria-valuenow="0" aria-valuemin="0" aria-valuemax="100"
          :style="{ width: contador + '%' }" :class="tipoBarra">
          {{ contador }}
        </div>
      </div>
      <button @click="contador++" class="btn btn-primary">+</button>
      <button @click="contador--" class="btn btn-danger">-</button>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data: () => ({
    contenido: "Hola mundo desde programador novato",
    seen: true,
    message: 'Hola Vue.js!',
    lenguajes: [
      { nombre: "JavaScript", link: 'https://www.javascript.com', puntos: 0 },
      { nombre: "PHP", link: 'https://php.net', puntos: 0 },
      { nombre: "Python", link: 'https://www.python.org', puntos: 0 }
    ],
    nuevoLenguaje: '',
    nuevoLink: '',
    colorFondo: 'bg-primary',
    cambioColor: false,
    texto: 'programador novato',
    contador: 0
  }),
  methods: {
    reverseMessage: function () {
      this.message = this.message.split('').reverse().join('')
    },
    agregarLenguaje() {
      this.lenguajes.push({ nombre: this.nuevoLenguaje, link: this.nuevoLink, puntos: 0 })
      this.nuevoLenguaje = '';
      this.nuevoLink = '';
    },
  },
  computed: {
    sumarTodo() {
      let total = 0;
      this.lenguajes.forEach(lenguaje => {
        total += lenguaje.puntos;
      })

      return total;
    },
    classArray: function () {
      return [
        this.cambioColor ? 'text-primary' : 'text-warning'
      ]
    },
    alReves() {
      return this.texto.split('').reverse().join('');
    },
    tipoBarra() {
      return {
        'bg-success': this.contador <= 10,
        'bg-warning': this.contador > 10 && this.contador <= 20,
        'bg-danger': this.contador > 20
      }
    },
  }
}
</script>

<style>

</style>
