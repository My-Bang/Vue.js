<script>
export default {
           // inject : ['message','reversedMessage'],

          inject: {
    customMessage: {
      from: 'message',
      default: 'default value',
    },
    customReversedMessage: {
      from: 'reversedMessage',
      default: 'default value',
    },
  },
};

</script>

<template>

  <h1>{{ customMessage }}</h1>
  <h2>{{ customReversedMessage }}</h2>
</template>

<style>
h1{
    color: blue;
}

p{
    color: green;
}
</style>