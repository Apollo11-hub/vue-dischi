<template>
  <section>
    <div class="container pt-5 d-flex"  v-if="isLoaded">
      <div class="row row-cols-6 w-100 h-75 d-flex justify-content-center  ">
        <main-component-card
        v-for="(music , index) in filteredArrayFunction" :key="`main-${index}`"
        :musicItem="music"
        ></main-component-card>
      </div>
    </div>
        <div class="loader w-100 h-100 d-flex justify-content-center align-items-center" v-else>
          <div class="lds-ellipsis">
            <div></div>
            <div></div>
            <div></div>
            <div></div>
          </div>
        </div>
  </section>
</template>

<script>
import MainComponentCard from './MainCompoent/MainComponentCard.vue';

export default {
  components: { MainComponentCard },
  name:'MainLayout',
  props:{
    isLoaded : Boolean,
    musicArray : Array,
    genreUserChoice : String,
    artistUserChoice : String
  },



  computed: {
    // filterdMusicArrayPerGenre(){
    //   let filtredGenre = [];
    //   if(this.genreUserChoice === ''){
    //     filtredGenre = this.musicArray;
    //   }else{
    //     filtredGenre = this.musicArray.filter(music =>{
    //       return music.genre === this.genreUserChoice;
    //     })
    //   }
    //   return filtredGenre;
    // },

    // filteredMusicArrayPerArtist(){
    //   let filteredArtist = [];
    //   if(this.artistUserChoice === ''){
    //     filteredArtist = this.musicArray;
    //   }else{
    //     filteredArtist = this.musicArray.filter(music =>{
    //       return music.author === this.artistUserChoice;
    //     })
    //   }
    //   return filteredArtist;
    // },


  filteredArrayFunction(){
    let filterArray = [];
    if(this.artistUserChoice === '' && this.genreUserChoice === ''){
      filterArray = this.musicArray;
    }else if ( this.artistUserChoice != '' && this.genreUserChoice === ''){
      filterArray = this.musicArray.filter(artist =>{
        return artist.author === this.artistUserChoice;
      })
    }else if ( this.artistUserChoice === '' && this.genreUserChoice != ''){
      filterArray = this.musicArray.filter(artist =>{
        return artist.genre === this.genreUserChoice;
      })
    }else{
      filterArray= this.musicArray.filter(array =>{
        return (array.genre.includes(this.genreUserChoice) && array.author.includes(this.artistUserChoice))
      } )
    }
    return filterArray
  }


  },

}
</script>

<style lang="scss" scoped>
@import '../assets/style/general';
@import '../assets/style/utilities';
  section{
    background-color:#1e2d3b ;
    min-height: calc(100vh - 84px);
    .container{
      height: 100%;
    }
    .loader{
      .lds-ellipsis {
        display: inline-block;
        position: relative;
        width: 80px;
        height: 80px;
        }
      .lds-ellipsis div {
        position: absolute;
        top: 33px;
        width: 13px;
        height: 13px;
        border-radius: 50%;
        background: #fff;
        animation-timing-function: cubic-bezier(0, 1, 1, 0);
      }
      .lds-ellipsis div:nth-child(1) {
        left: 8px;
        animation: lds-ellipsis1 0.6s infinite;
      }
      .lds-ellipsis div:nth-child(2) {
        left: 8px;
        animation: lds-ellipsis2 0.6s infinite;
      }
      .lds-ellipsis div:nth-child(3) {
        left: 32px;
        animation: lds-ellipsis2 0.6s infinite;
      }
      .lds-ellipsis div:nth-child(4) {
        left: 56px;
        animation: lds-ellipsis3 0.6s infinite;
      }
      @keyframes lds-ellipsis1 {
        0% {
          transform: scale(0);
        }
        100% {
          transform: scale(1);
        }
      }
      @keyframes lds-ellipsis3 {
        0% {
          transform: scale(1);
        }
        100% {
          transform: scale(0);
        }
      }
      @keyframes lds-ellipsis2 {
        0% {
          transform: translate(0, 0);
        }
        100% {
          transform: translate(24px, 0);
        }
      }
    }
  }
</style>