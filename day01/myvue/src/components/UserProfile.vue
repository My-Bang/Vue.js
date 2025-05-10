<script>
export default {
    emits : ['print-hello', 'onPrint-hello'],
    props : {
        name :{
        type :String,
        required : true,
        validator : function (value){
            return value.length > 1;
        },
    },

    age : {
        type : Number,
       default : function(){
        return 25;
       }
    },
  
    address : {
        type : String,
      
    },

    phoneNum :{
        type :String,
        required : true,
        validator : function (value){
            return value.length > 12;
        },
    },


},

methods : {
    parentEventCall1(){
        this.$emit('print-hello');
    },
    parentEventCall2(){
        this.$emit('onPrint-hello', {name : 'ssg',age : 30});

    },
}
    
}

</script>

<template>

<p>이름 : {{ name }}</p>
<p>나이 : {{ age }}</p>
<p>주소 : {{ address }}</p>
<p>전화번호 : {{ phoneNum }}</p>

<!-- <button @click="$emit('print-hello', 'ssg', 30)">클릭</button>  -->
<button @click="parentEventCall1">클릭</button>
<button @click="parentEventCall2">클릭</button>

</template>