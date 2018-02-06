<template>
    <div class="tool-bar">
        <div class="tool-left">
            <div class="item">
                <a href="http://127ad.com/web/raiders.html"><img class="f-img" src="../assets/raider.png"></a>
                攻略
            </div>

            <div class="item" @click="openProp">
                <img class="f-img" src="../assets/tool.png">
                道具屋
            </div>
        </div>

        <div class="tool-right">
            <div class="item" @click="addWater">
                <img class="r-img" src="../assets/water.png">
                水分
                <i v-if="props.water > 0">{{props.water}}</i>
                <div class="weight" :class="{'add-weight': wActive}">
                    +20g
                </div>
            </div>

            <div class="item" @click="addFertilizer">
                <img class="r-img" src="../assets/fertilizer.png">
                施肥
                <i v-if="props.fertilizer > 0">{{props.fertilizer}}</i>
                <div class="weight" :class="{'add-weight': fActive}">
                    +30g
                </div>
            </div>

            <div class="item" @click="addSun">
                <img class="r-img" src="../assets/sun.png">
                阳光
                <i v-if="props.sun > 0">{{props.sun}}</i>
                <div class="weight" :class="{'add-weight': sActive}">
                    +40g
                </div>
            </div>
        </div>

        <img class="watering" :class="{'w-active': wActive}" src="../assets/watering.png">
        <img class="fertilizing" :class="{'f-active': fActive}" src="../assets/fertilizing.png">
        <img class="shine" :class="{'s-active': sActive}" src="../assets/shine.png">
        <div class="dialog" :class="{'dialog-active': dialog}">
            {{alarm}}
        </div>
    </div>
</template>

<script>
    export default {
        props: ['props', 'user'],
        data() {
            return {
                wActive: false,
                fActive: false,
                sActive: false,
                dialog: false,
                alarm: '',
            }
        },
        methods: {
            openProp: function () {
                this.$emit("openProp");
            },
            addWater: function() {
                if (this.props.water > 0 && this.user.waterTime < this.props.useMax) {
                    this.$emit("addWeight", 20);
                    this.wActive = true;
                    setTimeout(() => {
                        this.wActive = false;
                    }, 3000);
                } else {
                    if (this.props.water < 1) {
                        this.alarm = "道具用完了，再去兑换一点吧！";
                    } else if (this.user.waterTime >= this.props.useMax) {
                        this.alarm = "今天水份够了，明天再来吧！";
                    }
                    this.dialog = true;
                    setTimeout(() => {
                        this.dialog = false;
                    }, 2000);
                }
            },
            addFertilizer: function() {
                if (this.props.fertilizer > 0 && this.user.fertilizerTime < this.props.useMax) {
                    this.$emit("addWeight", 30);
                    this.fActive = true;
                    setTimeout(() => {
                        this.fActive = false;
                    }, 3000);
                } else {
                    if (this.props.fertilizer < 1) {
                        this.alarm = "道具用完了，再去兑换一点吧！";
                    } else if (this.user.fertilizerTime >= this.props.useMax) {
                        this.alarm = "今天养份够了，明天再来吧！";
                    }
                    this.dialog = true;
                    setTimeout(() => {
                        this.dialog = false;
                    }, 2000);
                }
            },
            addSun: function() {
                if (this.props.sun > 0 && this.user.sunTime < this.props.useMax) {
                    this.$emit("addWeight", 40);
                    this.sActive = true;
                    setTimeout(() => {
                        this.sActive = false;
                    }, 3000);
                } else {
                    if (this.props.sun < 1) {
                        this.alarm = "道具用完了，再去兑换一点吧！";
                    } else if (this.user.sunTime >= this.props.useMax) {
                        this.alarm = "今天阳光够了，明天再来吧！";
                    }
                    this.dialog = true;
                    setTimeout(() => {
                        this.dialog = false;
                    }, 2000);
                }
            }
        }
    }
</script>

<style scoped>
    @keyframes watering{
        0% {opacity: 0; top: -100px; z-index:1000;}
        50% {opacity:1; top: -180px;}
        100% {opacity: 0; z-index: -1;}
    }

    @keyframes fertilizing{
        0% {opacity: 0; top: -100px; z-index:1000;}
        50% {opacity:1; top: -180px;}
        100% {opacity: 0; z-index:-1;}
    }

    @keyframes shine{
        0% {opacity: 0; z-index:1000;}
        50% {opacity:1;}
        100% {opacity: 0; z-index:-1;}
    }

    @keyframes weight{
        0% {opacity:0; top:0px;}
        40% {opacity:1; top: -200px;}
        60% {opacity:1; top: -200px;}
        100%{top: -600px; opacity: 0px;}
    }

    .tool-left {
        display: inline;
        float: left;
        margin-left: 15px;
    }
    .tool-right {
        display: inline;
        float: right;
        bottom: 0px;
        height: 90px;
        margin-right: 25px;
    }
    .item {
        display: inline-block;
        text-align: center;
        color: #fff;
        font-size: 12px;
        margin: 10px 10px 10px 0;
        position: relative;
    }
    .item i {
        display: inline-block;
        width: 12px;
        height: 12px;
        background-color: red;
        border: 1px #fff solid;
        border-radius: 50% 50%;
        position: absolute;
        top: 10px;
    }
    img {
        display: block;
    }
    .f-img {
        width: 40px;
    }
    .r-img {
        width: 35px;
        margin-top: 10px;
    }
    .watering {
        position: absolute;
        width: 150px;
        top: -100px;
        left: 50%;
        opacity: 0;
        z-index: -1;
    }
    .w-active {
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
    .add-weight {
        animation: weight 3s;
        animation-timing-function: ease;
    }
    .fertilizing{
        width: 100px;
        position: absolute;
        top: -100px;
        left: calc(50% - 150px);
        opacity: 0;
        z-index: -1;
    }
    .f-active {
        animation: fertilizing 2s;
    }
    .shine {
        height: 85%;
        width: 100%;
        position: fixed;
        top: 0px;
        left: -1%;
        opacity: 0;
        z-index: -1;
    }
    .s-active {
        animation: shine 2s;
    }
    .dialog {
        background-image: url("../assets/dialog-3.png");
        background-repeat: no-repeat;
        background-size: 100% 100%;
        padding: 0px 20px 15px;
        width: 150px;
        position: absolute;
        right: 30px;
        top: -40px;
        z-index: -1;
        opacity: 0;
    }
    .dialog-active {
        animation: shine 2s;
    }
</style>