<template>
      <div id="container">
          <div class="block centerContainer">
              <div class="left">
                  <Left />
              </div>
              <div class="right">
                  <Right :colorList='colorList'/>
              </div>
          </div>
          <div class="block" v-for="i in 36" :key="i">
                <div class="blockContent">
                    <!-- 
                    <img :src="'@/assets/images/home.png'" v-if="filterList(i).src">
                    -->
                    <div class="pullContent">
                        <div 
                            class="pull" 
                            v-for="x in 4" 
                            :key="x" 
                            :style="{'top': 0.4 + 'vw','left':(x * 0.5) + 'vw', 'color':pulColor(x).color, 'background':pulColor(x).background, 'border-color':pulColor(x).border}"
                            >
                            {{x}}
                        </div>
                    </div>

                    <img :src="getSrc(i)" v-if="filterList(i).src">
                    <div class="blockTop"></div>
                    <div class="blockBottom" :class="filterList(i).text && filterList(i).class" v-if="filterList(i).text">{{filterList(i).text}}</div> 
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
          colorList: [...colorJson]
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