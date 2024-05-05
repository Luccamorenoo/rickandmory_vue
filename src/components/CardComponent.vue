<script setup>
const personage = defineProps(["id", "image", "name", "status", "species", "origin", "location"]);
</script>


<template>
  <div class="col-6 mb-4 d-flex justify-content-center">
    <a v-bind:href="'/about/'+ personage.id" style="text-decoration:none">
      <div class="card shadow-sm card-scale" style="width: 35rem; background-color: #454545;">
        <div class="row">
            <div class="col">
              <img class="card-img-top img-card-justify" :src="personage.image" alt="Card image cap">
            </div>
            <div class="col">
              <div class="card-body">
                <h5 class="card-title text-light">{{personage.name}}</h5>
                <p class="card-text text-light">{{personage.status}} - {{ personage.species }}</p>
                <p class="card-text text-light">{{personage.origin.name}} - {{ personage.location.name }}</p>
              </div>
            </div>
        </div>
      </div>
    </a>
  </div>
</template>

<style>
  .text-light{
    color: #ffffff;
  }
</style>