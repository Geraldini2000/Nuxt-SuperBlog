<template>
  <div class="w-1/2 mx-auto my-20">
  <div>
    <button v-on:click="fetchSomething()" class="bg-red-500 p-3 text-white">
    Carregar artigos
    </button>
    <p></p>
  </div>

    <h1 class="text-3xl font-semibold text-red-600">{{ tituloBlog }}</h1>
    <article class="my-20" v-for="lista in listaArtigos" :key="lista.id">
      <h2 class="text-5xl font-semibold mb-5" > <span>Titulo do artigo: </span> {{lista.name}}</h2>
      <p class="mb-5"><span>Paragrafo do artigo: </span>{{lista.body}}</p>
      <p class="text-red-500">Ler Mais</p>
    </article>
  </div>
</template>

<script>
export default {
  data(){
    return {
      tituloBlog: 'Super Blog',
      listaArtigos: []
    }
  },
  methods: {
  async fetchSomething() {
    const listaArtigos = await this.$axios.$get('https://jsonplaceholder.typicode.com/comments')
    this.listaArtigos = listaArtigos
  }
}
}

</script>

<style scoped>
span {
  color: #f4f;
}
</style>
