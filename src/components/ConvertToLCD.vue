<script>
import { createVNode, render} from 'vue';
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
        /*-------------Making unique IDs for each canvas-------------*/
        this.counter += 1; 
        this.component_props.canvas_id = "number_canvas"+this.counter;
        /*-------------END : Making unique IDs for each canvas-------------*/
        /***
            NB : I presented a Number in LCD in format 
            as a canvas where i drew 3 horizontal rectangles
            and 4 vertical rectangles. Each rectangle have two states 0(Hidden)
            or 1(visible) and that depenps on the input value  ***/
        switch(this.received_input){
            case 0:
                this.component_props.horizontals = [1,0,1];
                this.component_props.verticals = [1,1,1,1];
                break;
            case 1:
                this.component_props.horizontals = [0,0,0];
                this.component_props.verticals = [1,0,1,0];
                break;
            case 2:
                this.component_props.horizontals = [1,1,1];
                this.component_props.verticals = [0,1,1,0];
                break;
            case 3:
                this.component_props.horizontals = [1,1,1];
                this.component_props.verticals = [0,1,0,1];
                break;
            case 4:
                this.component_props.horizontals = [0,1,0];
                this.component_props.verticals = [1,1,0,1];
                break;
            case 5:
                this.component_props.horizontals = [1,1,1];
                this.component_props.verticals = [1,0,0,1];
                break;
            case 6:
                this.component_props.horizontals = [1,1,1];
                this.component_props.verticals = [1,0,1,1];
                break;
            case 7:
                this.component_props.horizontals = [1,0,0];
                this.component_props.verticals = [0,1,0,1];
                break;
            case 8:
                this.component_props.horizontals = [1,1,1];
                this.component_props.verticals = [1,1,1,1];
                break;
            case 9:
                this.component_props.horizontals = [1,1,1];
                this.component_props.verticals = [1,1,0,1];
                break;
        }
        /*------------Draw programmatically a virtual node (canvas)-----------*/
        const container = document.createElement('div');
        container.setAttribute("style","display : inline-block;"); // To display numbers in rows 
        this.$refs.inputs_parent.appendChild(container);
        const vnode = createVNode(LCDNumber,this.component_props);// Virtaul Node from the component LCDNumber
        vnode.appContext = app._context;
        render(vnode,container);
        /*------------END : Draw programmatically a virtual node (canvas)-----------*/
    },
}
</script>
<template>
    <div ref="inputs_parent">

    </div>
</template>
