<script>
export default {
    props:{
        received_input : Number
    },
    updated(){
        console.log("Updated");
        /* if(!(Number.isInteger(this.received_input))){
            //alert("Only Numbers are accepted !");
        }   */    
    },
    data(){
        return{

        };
    }
}
</script>
<template>
    <h1>Received Input is : {{received_input}}</h1>
</template>