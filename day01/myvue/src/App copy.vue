<script>
export default{

data() {
  return {
    condition: 'C',
 visible: true, unvisible: false,
 fruits : ['apple', 'pear','orange'],
 user : {
  name : '강창선',
  age : 31,
  gender : 'male',
 }
  };
},
}
</script>
<template>
  <p v-if="condition === 'A'">A 입니다 .</p>
<p v-else-if="condition === 'B'">B 입니다 .</p>
<p v-else-if="condition === 'C'">C 입니다 .</p>
<p v-else> 조건에 해당하는 값이 없습니다 .</p>

<p v-if="visible"> 이 요소는 렌더링 됩니다.</p>
<p v-if="unvisible"> 이 요소는 렌더링 되지 않습니다.</p>

<h1> 과일 데이터의 반복 결과</h1>
<ul>
  <li v-for="(fruits, index) in fruits" :key="index">
    index : {{ index + 1 }} , value : {{ fruits }}
  </li>
</ul>
<br>
<ul>
  <li v-for="(value, key, index) in user" :key="index">
    {{ index + 1 }} : {{ key }} : {{ value }}
  </li>
</ul>

<br>
<ul>
  <li v-for="(value) in user">
    {{ value }}
  </li>
</ul>


</template>
<style>
.red-color{
  color: red;
}

</style>