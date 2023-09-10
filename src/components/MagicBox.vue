<template>
    <div class="animation-box" @click="createNewCircle">
        <div v-for="circle in circles" class="main_circle">
          <div class="small_circle"></div>
          <div class="small_circle"></div>
          <div class="small_circle"></div>
        </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        circles:{
          count:0
        }
      }
    },
    methods:{
      createNewCircle(){
        this.circles.count++;
      }
    }
  }
  </script>
  
  <style scoped>
  .animation-box {
    position: relative;
    width: 200px;
    height: 200px;
    background-color: #f0f0f0;
    display: flex;
    justify-content: center;
    align-items: center;
    cursor: pointer;
    overflow: hidden;
  }
  
  .main_circle {
    position: relative;
    width: 40px;
    height: 40px;
    background-color: #3498db;
    border-radius: 50%;
    animation: moveMainCircle 1.5s ease-in-out infinite;
  }
  .small_circle {
    width: 20px;
    height: 20px;
    background-color: #fff;
    left: 5px;
    top: 5px;
    position: absolute;
    border: 2px solid transparent;
    border-radius: 50%;
    animation-name: moveCircle;
    animation-duration: 1.5s;
    animation-timing-function:linear;
    animation-iteration-count:  infinite;
  }
  .small_circle:nth-child(1){
    animation-delay: 0.5s;
  }
  .small_circle:nth-child(2){
    animation-delay: 1s;
  }
  
  @keyframes moveCircle {
    0% {
      transform: rotate(0deg) translate(100px, 0);
    }
    100% {
      transform: rotate(360deg) translate(100px, 0);
    }
  }
  @keyframes moveMainCircle{
    0%,100%{
      transform:translate(0,0px);
    }
    50%{
      transform:translate(0,100px);
    }
  }
  </style>