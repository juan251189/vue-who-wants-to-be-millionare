<template>
<div id="score-component" class="score">
  <h1>Your Score</h1>


  <div class="score-div">
    <ul class="score-list">
      <li v-for="(item,i) in score" :key="i"
      :style="[scoretotal == i+1? {backgroundColor:'rgb(10, 162, 30,0.5)'} : '']">

        <div class="score-list-key" >{{i+1}}</div>

      <div style="float:right;width:50%; ">
      ${{item}}

      </div>
        </li>
    </ul>
  </div>
</div>
</template>
<script>
export default {
  props: ['scoretotal'],
  data() {
    return {
      score: [100.00, 200.00, 300.00, 500.00, 1000.00, 2000.00, 3000.00, 5000.00, 7000.00, 10000.00, 15000.00, 20000.00, 50000.00, 100000.00, 300000.00]
    }
  }



}
</script>
<style>
.score {
  min-width: 40%;
  height: 100%;
  position: absolute;
  right: 0px;
  top: 0px;
  z-index: 1;
  padding-right: 2%;
  background: linear-gradient(#040556, #00022A);
  opacity:0.95;


}

.score-list {
  display: flex;
  flex-direction: column-reverse;
  justify-content: center;


  color: #AD9757;
  font-weight: 700;
  font-size: 1.2em;
}

.score-div {
  width: 90%;
  margin: 0 auto;
  text-align: center;
  /*border: 1px solid white;*/
}

.score-list li {
  list-style: none;
  /*border: 1px solid white;*/
  width: 100%;



}

.score-list-key {
  margin-right: 10px;
/*border: 1px solid red;*/
float: left;
text-align: center;
  color: white;
}
@media only screen and (max-width: 700px) {
  .score {
    width: 70%;
  }
}
</style>
