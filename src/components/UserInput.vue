<script>
import ConvertToLCD from "./ConvertToLCD.vue"
export default{
    data(){
        return{
            input_value : null,
            toBesent_value : null,
            input_style : `transform: translate(${(window.innerWidth/2)-149}px, 30%);`,
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
            <h1>Numbers LCD Display</h1>
            <div v-bind:style="input_style">
                <label>Enter A Number Please ^_^  </label>
                <input id="numbers_input"
                    type="number" 
                    @keyup.prevent="getPressedNumber" 
                    v-model="input_value"
                />
            </div>
            <br/>
            <ConvertToLCD :received_input="toBesent_value"/>
        </div>  
</template>
<style scoped>
/* Chrome, Safari, Edge, Opera */
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

/* Firefox */
input[type=number] {
  -moz-appearance: textfield;
}

</style>