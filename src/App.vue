<template>
  <div>
    <HeaderLayout
    @choice="musicTypeSelected"
    />
    <MainLayout
      :musicArray="musicArray"
      :isLoaded="isLoaded"
      :musicUserChoice="musicUserChoice"
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
      isLoaded:false,
      musicUserChoice: ''
      
    }
  },
  methods: {
    getApi(){
      axios.get(this.baseUrl)
      .then(res =>{
        this.musicArray = res.data.response;
        this.isLoaded = true;
      })
    },
    musicTypeSelected(optionSelected){
      console.log('--->', optionSelected)
      this.musicUserChoice = optionSelected
    }

  },
  
}
</script>

<style lang="scss">
@import './assets/style/general';
@import './assets/style/utilities';

</style>
