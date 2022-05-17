<template>
  <section class="header-container">
    <div class="container-fluid py-4">
      <div class="row d-flex justify-content-between align-items-center">
        <img class="filter-green col-1 d-flex justify-content-between align-items-center" src="../assets/img/spotify.svg" alt="Spotify-logo">
        <select class="col-8 col-lg-3 col-xl-2 mx-3">
          <option selected>Open this select menu</option>
          <option value="1">One</option>
          <option value="2">Two</option>
          <option value="3">Three</option>
        </select>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "HeaderLayout"
}
</script>

<style lang="scss" scoped>
@import '../assets/style/general';
@import '../assets/style/utilities';
  .header-container{
    background-color: #2e3a46;
    .filter-green{
      width: 60px;
      filter: invert(60%) sepia(92%) saturate(361%) hue-rotate(84deg) brightness(86%) contrast(88%);
    }
    select{
      height: 30px;
      border-radius: 5px;

    }
  }

</style>