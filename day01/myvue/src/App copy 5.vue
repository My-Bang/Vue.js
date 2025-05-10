<script>
import FirstChild from './components/FirstChild.vue';

// export default {
//         components : {
//            FirstChild,
//         }   
       
//     }

export default {

     components : {
           FirstChild,
         },   

     data () {
           return {
               visible : true,
           };
     },
     
beforeCreate() {
     console.log('beforeCreate');
},

created() {
     
    setTimeout(()=> {
 
           this.visible = false;
    }, 3000);

},

// beforeMount() {
//      console.log('beforeMount');
// },

// mounted() {
//      console.log('mounted');
// },

// beforeUpdate() {
//      console.log('beforeUpdate');
// },
// updated() {
//      console.log('updated');
// },
// beforeUnmount() {
//      console.log('beforeUnmount');
// },
// unmounted() {
//      console.log('unmounted');
// },


}



</script>

<template>
       <FirstChild  v-if ="visible"/>
       <!-- <h1>나는 AppVue 의 주황색으로 칠해져야 하는 영역이야 </h1>
       <h1>나는 AppVue 의 주황색으로 칠해져야 하는 영역이야 </h1> -->
</template>

<style scoped>
    h1, p {
      color : orange !important;
    }
    
</style>