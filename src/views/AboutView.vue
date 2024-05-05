<script setup>
import { reactive, ref } from 'vue';
const personageProps = defineProps(["id"]);
let personage = reactive(ref());

function FetchAPi(personageId){
  fetch('https://rickandmortyapi.com/api/character/'+personageId)
  .then(response => response.json())
  .then(response => {
    console.log(response);
    personage.value = response;
  })
}
FetchAPi(personageProps.id);
</script>

<template>
  <div class="container mt-4">
    <button onclick="window.location.href ='/'" type="button" class="btn btn-light mb-4">Voltar</button>
   <div class="col-12 mb-4 d-flex justify-content-center">
      <div class="card shadow-sm" style="width: 80rem; height:30rem; background-color: #454545;">
        <div class="row">
            <div class="col">
              <img class="card-img-top img-card-justify-aqui" :src="personage.image" alt="Card image cap">
            </div>
            <div class="col">
              <div class="card-body">
                <h5 class="card-title text-light">{{ personage.name }}</h5>
                <p class="card-text text-light">Genero : {{ personage.gender }} - Status : {{ personage.status }} - Especie : {{ personage.species }}   </p>
                <p class="card-text text-light">Cidade : {{ personage.location.name }} - Planeta : {{ personage.origin.name }} </p>
              </div>
            </div>
        </div>
      </div>
      </div>
  </div>

</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}

.img-card-justify-aqui {
            object-fit: cover;
            object-position: 0 60%;
            height: 30rem;
        }
</style>
