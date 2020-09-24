<template>
  <div id="app">

    <div class="conteiner">
     <Timer
      v-for="timer of timers"
      v-bind:timer="timer"
      v-bind:key="timer.id"
    /> 

    <button class="add" v-on:click="addTimer">
      <span class="one"></span>
      <span class="two"></span>
    </button>
    </div>
    
  </div>
</template>

<script>
let arrTime = [
      {id: 1, hour: 0, minute: 0, sec: 0, run: false},
      {id: 2, hour: 0, minute: 0, sec: 0, run: false},
]
function addTimer(){
  let newTimer = {
    id: Date.now(),
    hour: 0,
    minute: 0,
    sec: 0,
    run: false,
  }
  arrTime.push(newTimer)
}

import Timer from '@/components/Timer'
export default {
  name: 'App',
  data() {
    return {
      timers: arrTime,
      addTimer
    }
  },
  components: {
      Timer,
      
  },  
}
setInterval(()=>{
  for (let timer of arrTime){
    if(timer.run){
        let newSec = timer.sec+1;
        let newMinute = timer.minute;
        newSec===60 ? (timer.sec=0, newMinute++) : (timer.sec++)

        if(newMinute===60){
          timer.minute=0
          timer.hour++
        }
        else{
          if(newSec===60) 
            timer.minute++
        }
        
    }
  }
  },1000)
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

#app {
  padding-left: 187px;;
  padding-right: 188px;
}
.conteiner {
  width: 100%;
  margin: auto;
  display: flex;
  flex-flow: row wrap;
  justify-content: left;
  align-items: center;
}
.add{
  position: relative;
  display: block;
  width: 225px;
  height: 120px;
  background-color: #696969;
  margin-right: 25px;
  margin-left: 25px;
  margin-top: 25px;
  margin-bottom: 25px;
}
span.one{
  position: absolute;
  width: 20px;
  height: 3px;
  background: black;
  display: block;
  left: 50%;
  transform: translate(-50%, -50%);
  background: #9E9E9E;
  
}
span.two{
  position: absolute;
  height: 20px;
  width: 3px;
  background: black;
  display: block;
  left: 50%;
  transform: translate(-50%, -50%);
  background: #9E9E9E;
}
@media (min-width: 768px) and (max-width: 1024px){
     #app {
  padding-left: 133px;;
  padding-right: 135px;
  } 
}
@media (min-width: 320px) and (max-width: 767px){
     #app {
  padding-left: 46px;
  padding-right: 49px;
} 

}
</style>
