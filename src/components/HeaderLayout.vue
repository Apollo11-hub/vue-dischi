<template>
  <section class="header-container">
    <div class="container-fluid py-4">
      <div class="row d-flex justify-content-between align-items-center">
        <img class="filter-green col-1 d-flex justify-content-between align-items-center" src="../assets/img/spotify.svg" alt="Spotify-logo">
        <select  
          v-model="musicGenreSelected" 
          @change="$emit('choiceGenre' , musicGenreSelected )" 
          class="col-8 col-lg-3 col-xl-2 mx-3">
          <option value="">Tutti i Generi</option>
          <option value="Rock">Rock</option>
          <option value="Pop">Pop</option>
          <option value="Jazz">Jazz</option>
          <option value="Metal">Metal</option>
        </select>
          <select
            v-model="musicArtistSelected"
            @change="$emit('choiceArtist', musicArtistSelected)"
            class="col-8 col-lg-3 col-xl-2 mx-3">
            <option value="">Tutti Gli Artisti</option>
            <option
              v-for="(artist, index) in musicArray" :key="`artist${index}`"
              :value="artist.author">{{artist.author}}</option>
          </select>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "HeaderLayout",
  props:{
    musicArray : Array,
  },

  data() {
    return {
      musicGenreSelected: '',
      musicArtistSelected: '',
    }
  },
  methods: {

  },
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