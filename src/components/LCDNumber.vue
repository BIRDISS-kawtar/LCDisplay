<script>
export default {
    props:{
        horizontals : Array,
        verticals : Array,
        canvas_id : String,
    },
    data(){
        return{
            canvas_width : 100,
            canvas_height : 200,
        }
    },
    mounted(){
        console.log("id is ",this.canvas_id);
        const canvas = document.getElementById(this.canvas_id);
        if (canvas.getContext) {
            const ctx = canvas.getContext('2d');
            // Horizontals
            for(let i=0;i<3;i++){
                if(this.horizontals[i] === 1){
                    ctx.fillRect(this.canvas_width/5,(this.canvas_height)*(9/20)*i,(this.canvas_width)*(3/5),this.canvas_height/10); // H1
                }
            }
            // Verticals 
            for(let i=0;i<4;i++){
                if(this.verticals[i] === 1){
                    if( i%2 == 0){// V1
                        let addition_odd = 1/10 + (i*(9/40));
                        ctx.fillRect(0,this.canvas_height*addition_odd,this.canvas_width/5,this.canvas_height*(7/20));
                    }else{// V2
                        let addition_even = 1/10 + ((i-1)*(9/40));
                        ctx.fillRect(this.canvas_width*(4/5),this.canvas_height*addition_even,this.canvas_width/5,this.canvas_height*(7/20));
                    }
                }
            }
            
        }

    }
}
</script>

<template>
    <canvas v-bind:id="canvas_id" v-bind:width="canvas_width" v-bind:height="canvas_height" style="border-style : solid">
    </canvas>
</template>