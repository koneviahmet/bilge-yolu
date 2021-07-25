<template>
      <div id="container">
          <div class="block centerContainer">
              <div class="left">
                  <Left />
              </div>
              <div class="right">
                  <Right />
              </div>
          </div>
          <div class="block" v-for="i in 36" :key="i">
                <div class="blockContent">
                    <!-- 
                    <img :src="'@/assets/images/home.png'" v-if="filterList(i).src">
                    -->

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

export default {
  name: 'App',
  data() {
      return {
          blockList: [...dataJson]
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


.block{
    opacity: 0.9;
    overflow: hidden;
    position: relative;
    border: solid 1px #ccc; 
    background: #f1f1f1; 
    padding: 2px; 
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
    background: #fff;
    flex: 1;
}


.centerContainer .right{
    background: #ccc;
    flex: 1;
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