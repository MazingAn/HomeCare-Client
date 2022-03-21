<template>
  <div id="dashboard">
    <div class="col-3">
      <div class="card-1x1 card-yellow"></div>
      <div class="card-1x1 card-purple"></div>
    </div>
    <div class="col-3">
      <div class="card-1x2 card-red"></div>
    </div>
    <div class="col-3">
      <div class="card-1x2 card-blue"></div>
    </div>
  </div>
</template>

<script></script>

<style scoped>
  #dashboard {
    height: calc(100vh - 120px);
    margin: 0 3%;
    display: flex;
    flex-direction: row;
    justify-content: center;
  }
  
  .col-3{
    display: flex;
    width: 32%;
    padding: 3% 1%;
    flex-direction: column;
  }

  .card-1x1 {
    display: flex;
    width: 100%;
    height: 46%;
    margin: 3% 0;
    border-radius: 20px;
  }

  .card-yellow{
    background-image: radial-gradient(#F0C960 10%, #FBDC2A 100%);
  }

  .card-purple{
    background-image: radial-gradient(#7B23DB 5%,#C15BED 100%);
  }

  .card-red{
    background-image: radial-gradient(#C15BED 5%,#FE479B 100%);
  }

  .card-blue{
    background-image: radial-gradient(#11AAF7 5%,#2556F8 100%);
  }

  .card-1x2 {
    display: flex;
    width: 100%;
    height: 95%;
    margin: 4% 0;
    border-radius: 20px;
  }
</style>
