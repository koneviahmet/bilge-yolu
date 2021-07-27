<template>
      <div id="container">
          <div class="block centerContainer">
              <div class="left">
                  <Left />
              </div>
              <div class="right">
                  <Right :colorList='colorList' :gamers='gamers'/>
              </div>
          </div>
          <div class="block" v-for="(block, i) in blockList" :key="i">
                <div class="blockContent">
                    <!-- 
                    <img :src="'@/assets/images/home.png'" v-if="filterList(i).src">
                    -->
                    <!----> 
                    <div class="pullContent">
                        <div 
                            class="pull" 
                            v-for="(gamer, x) in gamersFilter(getSira(i))" 
                            :key="x" 
                            :style="{'color':pulColor(gamer.pul).color, 'background':pulColor(x).background, 'border-color':pulColor(gamer.pul).border}"
                            >
                            {{gamer.pul}}
                        </div>
                    </div>
                     
                    <img :src="getSrc(block.index)" v-if="block.src">
                    <div class="blockTop"><!--{{getSira(i)}}--></div>
                    <div class="blockBottom" :class="block.text && block.class" v-if="block.text">{{block.text}}</div> 
                     
                </div>
          </div>
      </div>
</template>

<script>
import Left from './left'
import Right from './right'
import dataJson from './data.json';
import colorJson from './color.json';

export default {
  name: 'App',
  data() {
      return {
          blockList: [...dataJson],
          colorList: [...colorJson],
          gamers: [
              {
                  pul: 1,
                  sira: 0
              },
              {
                  pul: 2,
                  sira: 0
              },
              {
                  pul: 3,
                  sira: 1
              },
              {
                  pul: 4,
                  sira: 1
              }
          ]
      }
  },
  components: {
    Left,
    Right,
  },
  methods: {
        filterList(i){
            return this.blockList.filter(item => item.index == i)[0];
        },
        getSrc(i){
            return require('../assets/images/' + this.filterList(i).src);
        },
        pulColor(i){
            let kalan = parseInt(i) % this.colorList.length;
            return this.colorList[kalan];
        },
        gamersFilter(sira){
            return this.gamers.filter(i => i.sira == sira);
        },
        getSira(index){
            let newSira = [14,13,12,11,10,9,8,7,6,5,4,3,2,1,15,36,16,35,17,34,18,33,19,20,21,22,23,24,25,26,27,28,29,30,31,32];
            return newSira[index];
        }
  }
}
</script>



<style scoped>
#container{
    position: fixed;
    height: 100%;
    width: 100%;
    display: grid;
    grid-template: 1fr 1fr 1fr 1fr 1fr 1fr / 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr;
}

.pullContent{
    position: relative;
    width: 100%;
    height: 100%;
}

.pull{
    position: absolute;
    width: 2.4vw;;
    height: 2.4vw;;
    background: #9de6e8;
    border: solid 2px #73b9d7;
    color: #333;
    border-radius: 50%;
    text-align: center;
    font-size: 1.8vw;
}

.block{
    opacity: 0.9;
    overflow: hidden;
    position: relative;
    border: solid 1px #ccc; 
    background: #f1f1f1; 
    margin: 2px;
    font-size:  1.4vw;
}


.centerContainer{
    opacity: 1;
    background: none;
    border: none;
    grid-row: 2 / 6;
    grid-column: 2 / 14;
    display: flex;
    align-items: flex-end;
}


.centerContainer .left{
    flex: 1;
}


.centerContainer .right{
    flex: 1;
    width: 100%;
    height: 100%;
}



.blockContent{
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;

}

.blockContent img{
    width: 80%;
    position: absolute;
    bottom: -0.9vw;
    right: -0.9vw;
    opacity: .5;
}

.blockTop{
    flex: 3;
}

.blockBottom{
    background: blue;
    flex: 1;
    text-align: center;
    color:  #fff;
}

.red{
    background: #c93838;
}

.blue{
    background: #263859;
}

.green{
    background: #50CB93;
}

.yellow{
    background: #FFA900;
}
</style>