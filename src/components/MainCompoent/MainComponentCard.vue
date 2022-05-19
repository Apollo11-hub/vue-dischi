<template>
  <div class="col py-3">
    <div class="ap-card">
      <div class="img-container">
        <img :src="musicItem.poster" :alt="musicItem.author">
      </div>
      <p class="titolo mt-3">{{musicItem.title}}</p>
      <p class="sottotitolo mb-0">{{musicItem.author}}</p>
      <p class="ap-data">{{musicItem.year}}</p>
  </div>
</div>
</template>

<script>

export default {
  name:'MainComponentCard',
  props:{
    musicItem : Object,
  }
}
</script>

<style lang="scss" scoped>
@import '../../assets/style/general';
@import '../../assets/style/utilities';
  .col{
    margin: 25px 35px 25px 0;
    background-color: #2e3a46;
    .img-container{
      width: 190px;
      height: 200px;

    }
    .titolo{
      font-weight: 600;
      text-align: center;
      text-transform: uppercase;
      color:white
    }
    .sottotitolo,
    .ap-data{
      text-align: center;
      color: lightgray;
    }
  }
</style>