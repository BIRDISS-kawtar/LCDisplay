<script>
import ConvertToLCD from "./ConvertToLCD.vue"
export default{
    data(){
        return{
            input_value : null
        };
    },
    components:{
        ConvertToLCD
    },
    methods:{
        getPressedNumber(){

            console.log("-------------Pressed !--------------")
            console.log(`the input value is ${this.input_value}`);
            this.input_value = null;
            //document.getElementById("id").setAttribute("value",null);
        }
    },
    watch:{
        input_value:{
            handler(newValue){
                console.log("-------------Pressed !--------------");
            },
            immediate : true,
        }
    }

}
</script>

<template>
    <div>
        <input id="numbers_input" @keypress="getPressedNumber" v-model="input_value"/>
        <ConvertToLCD />
    </div>
</template>