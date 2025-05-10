<script>
import { handleError } from 'vue';

export default{

        data(){
          return{
          // inputStr : '',
            arr : [0,1,2],
            obj : {name : "minyeong"},
            primaryColor: 'red',
            primaryStyle : 'italic',
          };
        },

        watch : {
          // inputStr(newValue, odlValue){

          //       console.log(`old value : ${odlValue}`);
          //       console.log(`new value : ${newValue}`);



          //         },

          arr : {
              handler(newValue,odlValue){
                console.log(`old value : ${odlValue}`);
                console.log(`new value : ${newValue}`);
              },
              deep : true,
          },
         

          obj : {
            handler(newValue,odlValue){
                console.log(`old value : ${odlValue}`);
                console.log(`new value : ${newValue}`);
                  
              },
              deep: true,

      
            },

        },
      }
  
</script>
<template>
<input type="text" v-model="inputStr">
<h1 style="color: blue; font-style: italic;">{{ arr }}</h1>
<h1>{{ obj }}</h1>

<button @click="arr.push(3)">배열 변경</button>
<button @click="obj.age = 20">객체 변경</button>

<h1 :style="{color : primaryColor, fontStyle: primaryStyle}">inline style</h1>
<h1>Internal style</h1>
</template>
<style scoped>

/* h1{
  color : green;
  font-style: italic;
} */
/* @import './assets/main.css';
@import '../src/assets/main.css'; */
@import '@/assets/main.css';
@import '~/main.css';

</style>
