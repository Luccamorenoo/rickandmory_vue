<script>
export default {
  data() {
    return {
      imagemUrl: '/logo.png'
    };
  }
}
</script>

<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light border-bottom border-body">
    <div class="container-fluid">
      <img :src="imagemUrl" style="width: 5%; margin-right:10px">
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expended="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNav">
        <h2>The Rick and Morty API</h2>
      </div>
    </div>
  </nav>

  <div clas="main">
    <router-view></router-view>
  </div>

  <footer class="bg-light text-dark">
    <div> The Rick and Morty API</div>
  </footer>
  
</template>

<style>
footer{
  position: fixed;
  bottom: 0;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 56px;
}
</style>
