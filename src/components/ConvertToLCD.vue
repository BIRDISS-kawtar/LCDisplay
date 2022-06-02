<script>
export default {
    props:{
        received_input : Number
    },
    data(){
        return{
            //inputs : new Array(),
            //last_input : null
        };
    },
    updated(){
        console.log("updated",this.received_input);
        //this.inputs.push(this.received_input);
        const elt = document.createElement('p');
        elt.textContent = `Input Value =${this.received_input}`;
        this.$refs.inputs_parent.appendChild(elt);
    },
}
</script>
<template>
    <div ref="inputs_parent">

    </div>
</template>