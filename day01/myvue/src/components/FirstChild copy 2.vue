<script>

export default{
   data(){
    return{
        number : 5,
    };
   },
   computed : {
    doubleNum(){
            return this.number * 2;
    },
   },
   methods : {
    increment(){
        this.number++;
    },
   },


}

</script>

<template>
  <h1>{{ number }}</h1>
</template>

<style>
h1{
    color: blue;
}

p{
    color: green;
}
</style>