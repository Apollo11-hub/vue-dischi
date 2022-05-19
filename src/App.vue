<template>
  <div>
    <HeaderLayout
    :filteredArrayGenres="filteredArrayGenres"
    :filteredArrayArtists="filteredArrayArtists"
    @choiceGenre="musicTypeSelected"
    @choiceArtist="musicArtistSelected"
    />
    <MainLayout
      :musicArray="musicArray"
      :isLoaded="isLoaded"
      :genreUserChoice="genreUserChoice"
      :artistUserChoice="artistUserChoice"
    />

  </div>
</template>

<script>
import axios from 'axios';
import HeaderLayout from './components/HeaderLayout.vue'
import MainLayout from './components/MainLayout.vue'


export default {
  name: 'App',
  components: {
    HeaderLayout,
    MainLayout
    },
  mounted() {
    this.getApi()
  },
  data() {
    return {
      baseUrl: 'https://flynn.boolean.careers/exercises/api/array/music',
      musicArray:[],
      filteredArrayGenres:[],
      filteredArrayArtists:[],
      isLoaded:false,
      genreUserChoice: '',
      artistUserChoice:''
      
    }
  },
  methods: {
    getApi(){
      axios.get(this.baseUrl)
      .then(res =>{
        this.musicArray = res.data.response;
        console.log(this.musicArray);
        this.arrayFilteredGenreFunction();
        this.arrayFilteredArtistFunction();
        this.isLoaded = true;
      })
      .catch(err=>{
        console.log(err)
      })
    },


    arrayFilteredGenreFunction(){
      this.musicArray.forEach(artist => {
        if(!this.filteredArrayArtists.includes(artist.author)) this.filteredArrayArtists.push(artist.author)
      });
    },

    arrayFilteredArtistFunction(){
      this.musicArray.forEach(genre => {
        if(!this.filteredArrayGenres.includes(genre.genre)) this.filteredArrayGenres.push(genre.genre)
      });
    },

      
    musicTypeSelected(genreSelected){
      console.log('--->', genreSelected)
      this.genreUserChoice = genreSelected
    },
    musicArtistSelected(artistSelected){
      console.log('--->', artistSelected);
      this.artistUserChoice = artistSelected
    }


  },
  
}
</script>

<style lang="scss">
@import './assets/style/general';
@import './assets/style/utilities';

</style>
