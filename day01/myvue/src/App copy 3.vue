<script>
export default{

        data(){
          return{
            // fruits: ['banana','orange','apple'],
            // gender : 'male',
            // selectItem : 'cafeLatte',
            // message : '',
            fname: 'Bang',
            lname : 'MinYeong',
            numArr: [1,2,3,4,5],
          };
        },


        computed:{
          fullName() {
            console.log('computed fullname');
            return `${this.lname} ${this.fname}`
          },
          evenSum(){
          return this.numArr
          .filter((v) => v % 2 === 1)
          .reduce((acc,cur) => acc + cur, 0);
        },
        },
      

        methods : {
          login(){
              console.log(`id: ${this.uid}`);
              console.log(`id: ${this.upw}`);

             },

             printData(){
              console.log(this.selectItem);
             },

             onchangeHandler($event){
              this.message = $event.target.value;
             },
          }

          


        }
  
</script>
<template>

<!-- <form action="/loginForm1"> -->
    <!-- <textarea v-model="message"></textarea>
    <button type="button" @click="printData">데이터 출력</button> -->
    <!-- <label for="banana"><input type="checkbox" v-model="fruits" value="banana">banana</label>
    <label for="orange"><input type="checkbox" v-model="fruits" value="orange">orange</label>
    <label for="apple"><input type="checkbox" v-model="fruits" value="apple">apple</label>
    <button type="button" @click="printData">확인</button> -->

    <!-- <label for="male"><input type="radio" v-model="gender" value="male">남성</label>
    <label for="female"><input type="radio" v-model="gender" value="female">여성</label>
    <button type="button" @click="printData">확인</button>  -->

    <!-- <select v-model="selectItem">
      <option value="americano">아메리카노</option>
      <option value="espresso">에스프레소</option>
      <option value="cafeLatte">카페라떼</option>
     
    </select>
    <button type="button" @click="printData">확인</button> 
    </form> -->


    <!-- <input type="text" id="text" v-model="message">{{ message }} -->

    <!-- <input type="text" @input ="onchangeHandler($event)">{{ message }} -->

   <p>{{ lname }} {{ fname }}</p> 
   <p>{{ fullName }}</p>
   <h1>{{ numArr.filter((v) => v % 2 === 0).reduce((acc, cur) => acc+cur, 0) }}</h1>
   <h1>{{ evenSum }}</h1>





</template>
<style>
</style>
