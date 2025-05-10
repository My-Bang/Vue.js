<script>
// import FirstChild from '@/components/FirstChild.vue';
// import { message, reversedMessage } from './keys';
import FirstChild from './components/FirstChild.vue';
import MyChild1 from './components/MyChild1.vue';

export default {
  components: {
    FirstChild, MyChild1,
  },

  mounted(){
      console.log(this.$refs.childref);
      console.log(this.$refs.childNumOddAdd);
      console.log(this.$refs.getChildnum());

  },
  // provide() {
  //   return {
  //     [message]: this.message,
  //     [reversedMessage]: this.reversedMessage,
  //   };
  // },
  // data() {
  //   return {
  //     message: 'Hello, Vue JS!',
  //   };
  // },
  // computed: {
  //   reversedMessage() {
  //     return this.message.split('').reverse().join('');
  //   },
  // },

  data(){
    return{
      parentNum : 10,
    };
  },

  computed : {
    numOddEven(){
      return this.parentNum % 2 === 0 ? '짝수' : '홀수';
    },
  },

  methods :{
    getParentNum(){
      return this.parentNum;
    },
  },


};
</script>
<template>
  <FirstChild />
  <MyChild1 ref = "childref" />
</template>

<style scoped>

</style>