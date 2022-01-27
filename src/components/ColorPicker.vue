<template>
    <div class="container">
        <div :style="boardStyle" @click="pickColor">
            <!-- <div :style="pickerStyle"></div> -->
        </div>
        <div :style="previewStyle">
        </div>
        X:{{x}}
        <br/>
        Y:{{y}}
        <br/>
        <br/>
        R:{{pickedColor.r}}
        <br/>
        G:{{pickedColor.g}}
        <br/>
        B:{{pickedColor.b}}
    </div>
</template>
<script>
export default {
    name: "ColorPicker",
    data() {
        return {
            pickedColor:{
                r:0,
                g:0,
                b:0,
            },
            mainColor:{
                r:255,
                g:0,
                b:0,
            },
            width: 300,
            height: 150,
            x: 300,
            y: 150,
        }
    }, 
    computed:{
        boardStyle() {
            return{
                width: this.width+"px",
                height: this.height+"px",
                background: "linear-gradient(rgba("+this.mainColor.r+","+this.mainColor.g+","+this.mainColor.b+",1), rgba(0,0,0,1))",
                "mask-image": "linear-gradient(to left,rgba(255,255,255, 1), rgba(255,255,255,0))",
                border: "solid #FFF 1px",
            };
        },
        previewStyle() {
            return{
                width: this.height+"px",
                height: this.height+"px",
                background:"rgba("+this.pickedColor.r+","+this.pickedColor.g+","+this.pickedColor.b+",1)",
            }
        }
    },
    methods: {
        pickColor: function(event) {
            console.log(event);
            this.x=event.layerX;
            this.y=event.layerY;
            Object.keys(this.mainColor).forEach(key => {
                let value = (this.height-this.y)*(this.mainColor[key]/this.height);
                
                this.pickedColor[key]=value;
                // let hStep = (255-this.pickedColor[key])/255/this.width;
                // let vStep = this.pickedColor[key]/255/this.height|0;
                // let value = (this.x*hStep + this.y*value)/2
                // this.pickedColor[key]=value;
            });
        }
    },
};
</script>
<style>
.container{
    display: flex;
    flex-direction: row;
}
</style>
