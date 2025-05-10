<script>
export default{

data() {
  return {
   // message : '<h1>Hello 병곤!</h1>', 
  // className : 'red-color'

  id : 'title', class : 'red-color',
  };
},
}
</script>
<template>
<div v-html = "message"></div>
<div v-text = "message"></div>
<div v-pre> {{ message }}</div>
<h1 v-bind:class="className">Hello Vuejs</h1>
<h1 :id="id" :class="class">Hello, Wake up!!</h1>
<h1 :id :class>Hello, Wake up!! please!</h1>




</template>
<style>
.red-color{
  color: red;
}

</style>