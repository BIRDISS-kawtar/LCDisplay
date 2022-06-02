<script>
import ConvertToLCD from "./ConvertToLCD.vue"
export default{
    data(){
        return{
            input_value : null,
            toBesent_value : null
        };
    },
    components:{
        ConvertToLCD
    },
    methods:{
        getPressedNumber(event){
            // Assure that the input is an integer 
            this.input_value = parseInt(event.key);
            if(Number.isInteger(parseInt(this.input_value))){
                this.toBesent_value = this.input_value;
            }
            else {// For some exceptional cases like : -,+ and e 
                if(event.key != "F5"){// To not interpret refresh as an input
                    alert("Only numbers are accepted !")
                }
            } 
        }
    },

}
</script>

<template>
    <div>
        <input id="numbers_input"
               type="number" 
               @keyup.prevent="getPressedNumber" 
               v-model="input_value"
        />
        <ConvertToLCD :received_input="toBesent_value"/>
    </div>
</template>