<template>
  <div class="svetofor">
        <h1>Traffic Signal Light</h1>
      <div class="box">
        <div class="circle" :class="{'red': light === 'red'}"></div>
        <div class="circle" :class="{'yellow': light === 'yellow'}" style="font-size: 18px; color: white">{{count}}</div>
        <div class="circle" :class="{'green': light === 'green'}"></div>
      </div>
    </div>
</template>
<script setup lang="ts">
import {ref} from 'vue'
let light = ref('red')
let num = 3;
let count = ref(num)

let changeLight = () => {
  if (light.value === 'red') {
    light.value = 'yellow'
    count.value = num
  } else if (light.value === 'yellow') {
    light.value = 'green'
    count.value = num
  }
  else if (light.value === 'green') {
    light.value = 'red'
    count.value = num
  }
}

setInterval(changeLight, count.value*1000)
setInterval(() => {
  if (light.value === 'red') {
    count.value--
  } else if (light.value === 'yellow') {
    count.value--
  }
  else if (light.value === 'green') {
    count.value--
  }
}, 1000)

</script>
<style scoped>

.svetofor{
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-image: linear-gradient(#4cc191,#4188b1);
}

*{
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  font-family: 'Roboto', Arial;
}
h1{
  position: absolute;
  top: 0;
  text-align: center;
  padding-top: 100px;
  color: white;
}
.box{
  position: relative;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  align-items: center;
  width:80px ;
  height: 250px;
  background: #2c3e50;
  border-radius: 50px;
}
.circle{
  width: 45px;
  height: 45px;
  background-color: black;
  border-radius: 100%;
  display: flex;
  align-items: center;
  justify-content: center;

}
.red{
  background-color: #ff3822;
  box-shadow: 0 0 60px 10px #ff3822;
}
.yellow{
  background-color: #eeff03;
  box-shadow: 0 0 60px 10px #eeff03;
}
.green{
  background-color: #06ff59;
  box-shadow: 0 0 60px 10px #06ff59;
}

</style>
