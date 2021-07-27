<template>
    <div>
        <div class="leftContent" v-if="(!oyuncuSecmeDurumu && !zarDurumu)">
            <div class="leftCenter">
                <ul>
                    <li v-for="(msg, key) in messages" :key="key" v-html="msg"></li>
                </ul>
            </div>
            <div class="leftInput" v-if="!game">
                <input type="text" placeholder="Sınıf Mevcudu" v-model="oyuncuAdedi"/>
            </div>
            <div class="leftFooter">
                <button class="btn btn-danger" v-if="!game" @click="start(oyuncuAdedi)">Başla</button>
                <button class="btn btn-danger" v-if="game" @click="selectGamer()">Oyuncu Seç</button>
                <button class="btn btn-danger" v-if="game" @click="newGame()" hidden>Yeni Oyun</button>
            </div> 
        </div>

        <div class="selectContent" v-if="!(!oyuncuSecmeDurumu && !zarDurumu)">
            oyuncu seç content
        </div>
    </div>
</template>

<script>
export default {
    name: 'Left',
    data() {
        return {
            oyuncuAdedi: null
        }
    },
    props: {
        game: Boolean,
        oyuncuSecmeDurumu: Boolean,
        zarDurumu: Boolean,
        start: Function,
        newGame: Function,
        selectGamer: Function,
        messages: Array
    }
}
</script>

<style scoped>
.selectContent {
    margin: 0.4vw;
    border: solid 1px #ccc;
    border-radius: 5px;
    background: #fff;
}

.leftContent {
    margin: 0.4vw;
    border: solid 1px #ccc;
    border-radius: 5px;
    background: #fff;
}


.leftCenter{
    font-size: 1.2vw;
    padding: 0.8vw;
    border-bottom: solid 1px #ccc;
}

.leftCenter ul{
    margin-left: 1.2vw;
    list-style: disc;
}

.leftInput{
    font-size: 1.2vw;
    padding: 0.8vw;   
    border-bottom: solid 1px #ccc;
}

.leftInput input{
    width: 100%;
    padding: 0.4vw;
}

.leftFooter{
    overflow: hidden;
    font-size: 1.2vw;
    padding: 0.8vw;
}

.btn{
    cursor: pointer;
    float: right;
    font-size: 1.2vw;
    padding: 0.4vw 0.6vw;
}

.btn-danger{
    border-radius: 2px;
    border: solid 1px #dc3545;
    background: #dc3545;
    color: #fff;
}

</style>