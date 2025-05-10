<script>
import FirstChild from './components/FirstChild.vue';
export default{

  components : {
           FirstChild,
         }, 
      data(){
        return{
            domEl : null,

        };
      },

      mounted(){
      //  const domEl = document.querySelector('h1');

        // const domEl = this.$refs.domEl;
        // const text = this.$refs.domEl.innerText;
        // console.log(text);

        const childNum =  this.$refs.child.number;
        const childDoubleNum = this.$refs.child.doubleNum;
        console.log(`메서드 호출 전 : ${childNum}`);
        console.log(`메서드 호출 전 : ${childDoubleNum}`);
        setTimeout(() => {
          this.$refs.child.increment();
          console.log(`메서드 호출 전 : ${childNum}`);
          console.log(`메서드 호출 전 : ${childDoubleNum}`);

        })

      },

}
</script>
<template>
       
<h1 ref="domEl">h1 태그</h1>
<FirstChild ref = 'child'/>

</template>

<style scoped>
  
    
</style>