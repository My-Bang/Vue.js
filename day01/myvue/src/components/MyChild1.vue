<script>
export default{

    data(){
        return{
            childNum : 10,
        };
    },
    computed :{
            childNumOddAdd(){
                return this.childNum % 2 === 0 ? '짝수' : '홀수';
            },
    },
        methods :{
            getChildnum(){
                return this.childNum;
            },
        },

        mounted(){
            console.log(this.$parent.parentNum);
            console.log(this.$parent.numOddEven);
            console.log(this.$parent.getParentNum());

        },

}

</script>

<template>
<h1>MyChild1</h1>
<h1>ParentChild</h1>

</template>