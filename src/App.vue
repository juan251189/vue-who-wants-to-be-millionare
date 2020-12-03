<template>
<div id="app">
  <button class="btn btn-score btn-primary" @click="scoreShow=!scoreShow">Score</button>
  <div class="container">
    <div class="row">
      <div class="col-12">
        <h1>The Super Quiz</h1>
      </div>
    </div>

    <transition name="fade">
      <app-score v-if="scoreShow" :scoretotal="score"></app-score>
    </transition>

    <component @nextquestion="nextQuestion" :index="index" :question="currentQuestion" :is="submitted" >
    </component>

  </div>


</div>
</template>

<script>
import Answer from './components/Answer.vue'
import Question from './components/Question.vue'
import Score from './components/Score.vue'
export default {
  name: 'App',
  data() {
    return {
      submitted: 'app-question',
      index: 0,
      currentQuestion: {},
      total: 0,
      score: 0,
      quantity:54,
      scoreShow: false,
      questions: [{
          Question: "Whats the capital of Colombia",
          answers: {
            a: 'Medellin',
            b: 'Cartagena',
            c: 'Bogota',
            d: 'Cali',

          },
          solution: 'Bogota'
        },
        {
          Question: "What's 45 +20",
          answers: {
            a: 65,
            b: 42,
            c: 37,
            d: 44,

          },
          solution: 65
        },
        {
          Question: "What's 80 +11",
          answers: {
            a: 35,
            b: 42,
            c: 91,
            d: 44,

          },
          solution: 91
        }
      ]

    }
  },
  methods: {
    nextQuestion() {
    this.scoreShow=true;
    var v =this;
      v.score += 1;
      setTimeout(function(){
        v.index+=1;
        v.currentQuestion=v.questions[v.index];
        v.scoreShow=false;
      }, 3000);
    }
  },
  components: {
    appAnswer: Answer,
    appQuestion: Question,
    appScore: Score

  },

  filters: {
    capitalized: function(value) {
      return value.toUpperCase();
    }
  },
  created() {
    //do something after creating vue instance
    this.currentQuestion = this.questions[this.index];
  }

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: rgb(209, 209, 209);
  margin-top: 60px;
}

body {
  background: url('./assets/background-room.jpg');
  background-size: cover;
  height: 100vh;
  background-repeat: no-repeat;
  background-position:center;
  padding-top: 10%;
  overflow: hidden;


}

.sign {
  width: 80%;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  background-color: #2e26a4;
  margin: 20px auto;
  color: #ddd9e3;
  padding: 20px;
  font-size: 2rem;
}

.btn-score {
  border-radius: 1px 20px 20px 1px;
  position: fixed;
  left: 1px;
  top: 10%;
  z-index: 2;
  transition:2.5s;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity .4s;
}

.fade-enter,
.fade-leave-to

/* .fade-leave-active below version 2.1.8 */
  {
  opacity: 0;
}

.slide-enter {
  opacity: 0;
  transition: 2s;
}

.slide-leave {}

.slide-enter-active {
  animation: slide-in 1s forwards;
  transition: opacity .5s;
}

.slide-leave-active {
  animation: slide-out 1s ease-out forwards;
  transition: opacity .5s;
  opacity: 0;
}

@media only screen and (max-width:450px){
body{
    padding-top: 40%;
}
.btn-score{
  top:10px;
}

}

@keyframes slide-in {
  from {
    transform: translateY(20px);
    width: 100%;
  }

  to {
    transform: translateY(0);
    width: 80%;
  }
}


@keyframes slide-out {
  from {
    transform: translateY(0);

  }

  to {
    transform: translateY(20px);

  }
}
</style>
