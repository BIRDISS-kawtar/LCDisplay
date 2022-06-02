<script>
import { createVNode, isVNode, render, ref, createApp,h} from 'vue';
import app from '../main'
import LCDNumber from './LCDNumber.vue';
export default {
    props:{
        received_input : Number
    },
    data(){
        return{
            counter : 0,
            component_props : {
                horizontals : [],
                verticals : [],
                canvas_id : "",
            }
        };
    },
    updated(){
        this.counter = this.counter +1;
        this.component_props.horizontals = [1,1,1];
        this.component_props.verticals = [1,1,1,1];
        this.component_props.canvas_id = "number_canvas"+this.counter;
        console.log("updated",this.component_props);
        const container = document.createElement('div');
        this.$refs.inputs_parent.appendChild(container);
        const vnode = createVNode(LCDNumber,this.component_props);
        vnode.appContext = app._context;
        render(vnode,container);
    },
}
</script>
<template>
    <div ref="inputs_parent">

    </div>
</template>