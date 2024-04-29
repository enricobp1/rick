<script setup>
    const personagens = defineProps(["nome", "imagem", "status", "especie", "genero", "localizacao", "episodio"])
    
</script>

<template>
    <div class="col-md-3">
        <div class="card mb-2" style="width: 18rem; height: 38rem">
            <img :src="personagens.imagem" alt="..." class="card-img-top">
            <div class="card-body">
                <h3 class="card-title text-center">Name: <br>{{ personagens.nome }}</h3>
                <h5 class="card-title text-center"> {{ personagens.status }} | {{ personagens.especie }}</h5>
                
                <h5 class="card-title text-center">Gender: {{ personagens.genero }}</h5>
                <h5 class="card-title text-center">Actual Location: {{ personagens.localizacao }}</h5>
                <h6 v-if="personagens.episodio == 1" class="card-title text-center">Appeared: {{ personagens.episodio }} Episode</h6>
                <h6 v-else class="card-title text-center">Appeared: {{ personagens.episodio }} Episodes</h6>
            </div>
        </div>
    </div>
</template>

<style>
    .card-body{
        background-color: #404a4e;
        color: #61d6e6;
    }
</style>