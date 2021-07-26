<template>
    <div class="rightContent"> 
        <div class="pullContent">
            <div 
                class="pull" 
                v-for="x in 15" 
                :key="x" 
                :style="{'color':pulColor(x).color, 'background':pulColor(x).background, 'border-color':pulColor(x).border}"
                >
                {{x}}
            </div>
        </div>
    </div>
</template>


<script>
export default {
    name: 'Right',
    props: {
        colorList: Array
    },
    data() {
        return {
            
        }
    },
    methods:{
        pulColor(i){
            let kalan = parseInt(i) % this.colorList.length;
            return this.colorList[kalan];
        }
    }
    
}
</script>


<style scoped>

.rightContent{
    position: relative;
    width: 100%;
    height: 100%;
}

.pullContent{
    background: #fff;
    border: solid 1px #ccc;
    border-radius: 5px;
    padding: 1vw;
    margin: 1vw;
    position: relative;
    display: grid;
    grid-template: 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr / 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr;
}

.pull{
    margin: 0.2vw;
    background: #9de6e8;
    border: solid 2px #73b9d7;
    color: #333;
    border-radius: 50%;
    text-align: center;
    font-size: 2.3vw;
}

</style>