<template>
  <section>
    <div class="container pt-5 d-flex"  v-if="isLoaded">
      <div class="row row-cols-6 w-100 h-75 d-flex justify-content-center  ">
        <main-component-card
        v-for="(music , index) in filterdMusicArray" :key="`main-${index}`"
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
    musicUserChoice : String
  },
mounted() {
  console.log(this.musicArray.genre)
},



  computed: {
    filterdMusicArray(){
      let filtredGenre = [];
      if(this.musicUserChoice === 'start'){
        filtredGenre = this.musicArray;
      }else{
        filtredGenre = this.musicArray.filter(music =>{
          return music.genre === this.musicUserChoice;
        })
      }
      return filtredGenre;
    }

  },

}
</script>

<style lang="scss" scoped>
@import '../assets/style/general';
@import '../assets/style/utilities';
  section{
    background-color:#1e2d3b ;
    height: calc(100vh - 84px);
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