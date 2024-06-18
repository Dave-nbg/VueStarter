<template>
  <h1>
    {{quizData[questionNumber].question}}
  </h1>

<div>
<li v-for="(listitem, index) in quizData[questionNumber].options" :key="index">
  <label>{{listitem}}</label>
  <input :value="listitem" v-model="selectedOption" type="radio"/>
</li>
</div>
<input type="button" value="ADD" @click="submitQuestion()" />
  <div v-if="questionCorrect === 'correct'">
    <p>Goede antwoord</p>
  </div>
  <div v-if="questionCorrect === 'fout'">
    <p>Antwoord fout</p>
  </div>


</template>

<script setup>
  import {ref} from "vue";
  import quizData from "@/Data/QuizData";

  const questionNumber = ref(getRandomInt(quizData.length));
  const selectedOption = ref("");
  const questionCorrect = ref("");

  function getRandomInt(max) {
    return Math.floor(Math.random() * max);
  }

  function getNewQuestion(){
    let number = getRandomInt(4);
    if(number !== questionNumber.value){
      questionNumber.value = (number)
    }
    else if(number === 0){
      questionNumber.value = (number+1)
    }
    else {
      questionNumber.value = (number-1)
    }
    selectedOption.value = ("");
    questionCorrect.value = ("");
  }

  function submitQuestion(){
    console.log(selectedOption.value)
    if(selectedOption.value === quizData[questionNumber.value].correctAnswer){
      questionCorrect.value = ("correct");
      getNewQuestion();
    }
    else{
      questionCorrect.value = ("fout")
    }
  }



</script>