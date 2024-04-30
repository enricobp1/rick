<script setup>
import {ref, reactive, onMounted } from 'vue'
import ListaPersonagem from '../components/ListaPersonagens.vue'

let personagens = reactive(ref(([])))
let pagina = ref(1)

const carregarPersonagens = (pagina) => {
  fetch(`https://rickandmortyapi.com/api/character/?page=${pagina}`)
    .then(response => response.json())
    .then(response => {
      personagens.value = response.results
    });
};

onMounted(() => {
  carregarPersonagens(pagina.value);
});

const ProximaPagina = () => {
  pagina.value++;
  carregarPersonagens(pagina.value);
};

const PaginaAnterior = () => {
  if (pagina.value > 1) {
    pagina.value--;
    carregarPersonagens(pagina.value);
  }
};

</script>


<template>
  <main>
    <div class="container">
        <div class="row mt-4">
          <ListaPersonagem
          v-for="personagem in personagens"            
          :nome="personagem.name"
          :imagem="personagem.image"
          :status="personagem.status"
          :especie="personagem.species"
          :genero="personagem.gender"
          :localizacao="personagem.location.name"
          :episodio="personagem.episode.length"
          >
          </ListaPersonagem>
        </div>  
      </div>
    

    

  <div class="pagination mt-2">
    <button class="btn btn-secondary btn-lg" @click="PaginaAnterior" :disabled="paginaAtual === 1">Página Anterior</button>
    <p class="texto-pagina">Current Page: {{ pagina }}</p>
    <button class="btn btn-primary btn-lg" @click="ProximaPagina">Próxima Página</button>
    </div>
  </main>
</template>

<style>
  .pagination {
    margin-left: 35%;
    margin-right: 35%;
  }

  .texto-pagina {
    font-size: 20px;
    text-align: center;
    color: #34acb4;

  }

</style>
