<script>
import SecondChild from '@/components/SecondChild.vue';
import { message,reversedMessage } from '@/keys';
export default {

  components: {
    SecondChild,
  },
  provide() {
    return {
      message: this.message,
      reversedMessage: this.reversedMessage,
    };
  },
  data() {
    return {
      message: 'Hello, SecondChild!',
    };
  },
  computed: {
    reversedMessage() {
      return this.message.split('').reverse().join('');
    },
  },
  inject: {
    customMessage: {
      from: message,
      default: 'default value',
    },
    customReversedMessage: {
      from: reversedMessage,
      default: 'default value',
    },
  },
};
</script>
<template>
         <h1>{{ customMessage }}</h1>
         <h2>{{ customReversedMessage }}</h2>
 <SecondChild />
</template>
<style>
     h1 {
        color: blue;
     }
     p {
         color: green;
     }
     
</style>