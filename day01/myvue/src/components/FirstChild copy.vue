<script>

export default{
    beforeUnmount(){
        console.log('beforeUnmount');
    },
    unmounted(){
        console.log('unmounted');

    },


}

</script>

<template>
    <!-- <h1>컴포넌트</h1>
    <p>내가 만든 첫 번째 컴포넌트</p> -->

<h1>First Child</h1>

</template>

<style>
h1{
    color: blue;
}

p{
    color: green;
}
</style>