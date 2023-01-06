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
        <a :href="lenguaje.link" target="_blank">{{ lenguaje.nombre }}</a>
      </li>
    </ul>
  </div>
</template>

<script>

export default {
  name: 'App',
  data: function () {
    return {
      contenido: "Hola mundo desde programador novato",
      lenguajes: [
        { nombre: "JavaScript", link: 'https://www.javascript.com', puntos: 0 },
        { nombre: "PHP", link: 'https://php.net', puntos: 0 },
        { nombre: "Python", link: 'https://www.python.org', puntos: 10 }
      ],
      nuevoLenguaje: '',
      nuevoLink: '',
    };
  },
  methods: {
    agregarLenguaje() {
      this.lenguajes.push({ nombre: this.nuevoLenguaje, link: this.nuevoLink })
      this.nuevoLenguaje = '';
      this.nuevoLink = '';
    }
  },
}
</script>

<style>

</style>
