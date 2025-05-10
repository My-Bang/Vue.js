<script>
export default{

        data(){
          return{
              name :'철수',
              gender : '남자',
              age : 20,
          };
        },

        methods : {
          increment(){
              this.number++;
          },
        }
            }
  
</script>
<template>

<div v-memo="[name, gender]">
<p>이름 : {{ name }}</p>
<p>성별 : {{ gender }}</p>
<p>나이 : {{ age }}</p>
</div>


<button @click="name = '영희'">이름변경</button>
<button @click="gender = '여자'">성별 변경</button>
<button @click="age = 25">나이 변경</button>

</template>
<style>
</style>
