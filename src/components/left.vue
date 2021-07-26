<template>
    <div class="leftContent">
        <div class="leftHeader">Header</div>
        <div class="leftCenter">
            <ul>
                <li>açıklama 1</li>
                <li>açıklama 2</li>
                <li>açıklama 3</li>
                <li>açıklama 4</li>
            </ul>
        </div>
        <div class="leftInput">
            <input type="text" placeholder="Sınıf Mevcudu"/>
        </div>
        <div class="leftFooter">
            <button class="btn btn-danger">Başla</button>
        </div> 
    </div>
</template>

<style scoped>
.leftContent {
    margin: 0.4vw;
    border: solid 1px #ccc;
    border-radius: 5px;
    background: #fff;
}

.leftHeader{
    font-size: 1.4vw;
    color: #fff;
    background: #263859;
    padding: 0.3vw 0.4vw;
    border-bottom: solid 1px #ccc;
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