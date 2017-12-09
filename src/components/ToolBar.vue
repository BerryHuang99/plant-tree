<template>
    <div class="tool-bar">
        <div class="tool-left">
            <div class="item">
                <img class="f-img" src="../assets/raider.png">
                攻略
            </div>

            <div class="item">
                <img class="f-img" src="../assets/tool.png">
                道具屋
            </div>
        </div>

        <div class="tool-right">
            <div class="item">
                <img class="r-img" src="../assets/water.png">
                水分
                <img class="watering" src="../assets/watering.png">
                <div class="weight">
                    +20g
                </div>
            </div>

            <div class="item">
                <img class="r-img" src="../assets/fertilizer.png">
                施肥
            </div>

            <div class="item">
                <img class="r-img" src="../assets/sun.png">
                阳光
            </div>
        </div>
    </div>
</template>

<script>
    export default {

    }
</script>

<style scoped>
    @keyframes watering{
        0% {opacity: 0; top: -100px;}
        20% {opacity:1; top: -160px;}
        40% {transform:rotate(35deg);}
        80% {transform:rotate(-35deg);}
        90% {transform:rotate(0deg);}
        100% {opacity: 0;}
    }

    @keyframes weight{
        0% {opacity:0; top:0px;}
        50% {opacity:1; top: -300px;}
        100%{top: -600px; opacity: 0px;}
    }

    .tool-left {
        display: inline;
        float: left;
    }
    .tool-right {
        display: inline;
        float: right;
    }
    .item {
        display: inline-block;
        text-align: center;
        color: #fff;
        font-size: 12px;
        margin: 10px 10px 10px 0;
        position: relative;
    }
    img {
        display: block;
    }
    .f-img {
        width: 50px;
    }
    .f-img:hover {
        width: 55px;
    }
    .r-img {
        width: 40px;
        margin-top: 10px;
    }
    .r-img:hover {
        width: 45px;
    }
    .watering {
        position: absolute;
        width: 150px;
        top: -100px;
        opacity: 0;
    }
    .item:hover .watering {
        animation: watering 2s;
    }
    .weight {
        position: absolute;
        background-color: #00baff;
        border: #fff solid 2px;
        width: 30px;
        height: 30px;
        border-radius: 50% 50%;
        line-height: 30px;
        opacity: 0;
    }
    .item:hover .weight {
        animation: weight 4s;
    }
</style>