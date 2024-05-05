<script setup>
import { onMounted, reactive, ref } from 'vue';
import CardComponent from '../components/CardComponent.vue';

let personage = reactive(ref());
var pages = 1;
var lastPage = 0;
var buttonPrevious;
var buttonNext;

onMounted(() => {
  FetchAPi(1);
  buttonPrevious = document.querySelector('#buttonPrevious');
  buttonNext = document.querySelector('#buttonNext');
  buttonPrevious.disabled = true;
})

function NextPage(page){

  buttonPrevious.disabled = false;

  page = page + 1;

  if (page == lastPage) buttonNext.disabled = true;
  
  FetchAPi(page)

  pages = page;
}

function PreviousPage(page){

  if (buttonNext.disabled == true) buttonNext.disabled = false;

  page = page - 1;
  
  if (page == 1) buttonPrevious.disabled = true;

  FetchAPi(page)

  pages = page;
}

function FetchAPi(page){
  fetch('https://rickandmortyapi.com/api/character/?page='+page)
  .then(response => response.json())
  .then(response => {
    personage.value = response.results;
    lastPage = response.info.pages;
  })
}
</script>

<template>
  <main>
    <div class="container">

      <div class="mt-4 d-flex justify-content-around">
        <button id="buttonPrevious" type="button" v-on:click="PreviousPage(pages)" class="btn btn-light">Anterior</button>
        <p class="text-light">Pagina {{ pages }} </p>
        <button id="buttonNext" type="button" v-on:click="NextPage(pages)" class="btn btn-light">Próximo</button>
      </div>

      <div class="row mt-4">
        <div class="col-sm-12">
          <div class="card-body row ">
            <CardComponent v-for="item in personage" 
              :key="item.id"
              :image="item.image"
              :name="item.name"
              :status="item.status"
              :species="item.species"
              :origin="item.origin"
              :location="item.location"
              :id="item.id"
              />
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<style>
        .card-scale:hover {
            transform: scale(1.1);
        }
        .img-card-justify {
            object-fit: cover;
            object-position: 0 80%;
            height: 225px;
        }
        .text-light{
    color: #ffffff;
  }
</style>
