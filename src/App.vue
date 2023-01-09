<template>
  <div id="app">
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
  </div>
</template>

<script>

export default {
  name: 'App',
  data: () => ({
    contenido: "Hola mundo desde programador novato",
    lenguajes: [
      { nombre: "JavaScript", link: 'https://www.javascript.com', puntos: 0 },
      { nombre: "PHP", link: 'https://php.net', puntos: 0 },
      { nombre: "Python", link: 'https://www.python.org', puntos: 0 }
    ],
    nuevoLenguaje: '',
    nuevoLink: ''
  }),
  methods: {
    agregarLenguaje() {
      this.lenguajes.push({ nombre: this.nuevoLenguaje, link: this.nuevoLink, puntos: 0 })
      this.nuevoLenguaje = '';
      this.nuevoLink = '';
    },
  },
  computed: {
    sumarTodo() {
      let total = 0;
      this.lenguajes.forEach( lenguaje => {
        total += lenguaje.puntos;
      })
      
      return total;
    }
  }
}
</script>

<style>

</style>
