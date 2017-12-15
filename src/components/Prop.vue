<template>
    <div class="prop" :class="{'close': isClose}">
        <div class="prop-room">
            <div class="prop-head">   
                <span>道具屋</span>
                <br>
                （目前拥有{{power}}点肾能量）
                <div class="close-button" @click="close()">&times;</div>
                <hr>
            </div>

            <div class="prop-body">
                <div class="alarm">{{alarm}}</div>
                
                <div class="item">
                    <span>小小水滴</span>
                    <div class="illustrate">
                        增加20g树木重量
                    </div>
                    <img src="../assets/water.png">
                    <div class="add">
                        <i @click="reduceWater">-</i>
                        {{water}}滴
                        <i @click="plusWater">+</i>
                    </div>
                    <div class="submit" @click="exchangeWater">
                        <span>点击兑换</span>
                        <br>
                        （每滴需要20点肾能量）
                    </div>
                </div>

                <div class="item">
                    <span>化肥</span>
                    <div class="illustrate">
                        增加30g树木重量
                    </div>
                    <img src="../assets/fertilizer.png">
                    <div class="add">
                        <i @click="reduceFertilizer">-</i>
                        {{fertilizer}}份
                        <i @click="plusFertilizer">+</i>
                    </div>
                    <div class="submit" @click="exchangeFertilizer">
                        <span>点击兑换</span>
                        <br>
                        （每份需要30点肾能量）
                    </div>
                </div>

                <div class="item">
                    <span>阳光</span>
                    <div class="illustrate">
                        增加40g树木重量
                    </div>
                    <img src="../assets/sun.png">
                    <div class="add">
                        <i @click="reduceSun">-</i>
                        {{sun}}份
                        <i @click="plusSun">+</i>
                    </div>
                    <div class="submit" @click="exchangeSun">
                        <span>点击兑换</span>
                        <br>
                        （每份需要40点肾能量）
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        props: ['isClose', 'props', 'power'],
        data() {
            return {
                alarm: '',
                water: 1,
                fertilizer: 1,
                sun: 1
            }
        },
        methods: {
            close: function () {
                this.alarm = '';
                this.water = 1;
                this.fertilizer = 1;
                this.sun = 1;
                this.$emit("closeProp");
            },
            reduceWater: function () {
                this.alarm = '';
                if (this.water > 1)
                    this.water--;
            },
            reduceFertilizer: function () {
                this.alarm = '';
                if (this.fertilizer > 1)
                    this.fertilizer--;
            },
            reduceSun: function () {
                this.alarm = '';
                if (this.sun > 1)
                    this.sun--;
            },
            plusWater: function () {
                if (this.water < this.props.propMax) {
                    this.alarm = '';
                    this.water++;
                } else {
                    this.alarm = "最多可购" + this.props.propMax + '滴';
                }
            },
            plusFertilizer: function () {
                if (this.fertilizer < this.props.propMax) {
                    this.alarm = '';
                    this.fertilizer++;
                } else {
                    this.alarm = "最多可购" + this.props.propMax + '份';
                }
            },
            plusSun: function () {
                if (this.sun < this.props.propMax) {
                    this.alarm = '';
                    this.sun++;
                } else {
                    this.alarm = "最多可购" + this.props.propMax + '份';
                }
            },
            exchangeWater: function () {
                if (this.water + this.props.water > this.props.propMax) {
                    this.alarm = "超出兑换限度，请用完再来兑换";
                } else if(this.water * 20 > this.power) {
                    this.alarm = "肾能量不足";
                } else {
                    this.$emit('plusWater', this.water);
                    this.water = 1;
                    this.alarm = '';
                    this.$emit("closeProp");
                }
            },
            exchangeFertilizer: function() {
                if (this.fertilizer + this.props.fertilizer > this.props.propMax) {
                    this.alarm = "超出兑换限度，请用完再来兑换";
                } else if(this.fertilizer * 30 > this.power) {
                    this.alarm = "肾能量不足";
                } else {
                    this.$emit('plusFertilizer', this.fertilizer);
                    this.fertilizer = 1;
                    this.alarm = '';
                    this.$emit("closeProp");
                }
            },
            exchangeSun: function() {
                if (this.sun + this.props.sun > this.props.propMax) {
                    this.alarm = "超出兑换限度，请用完再来兑换";
                } else if(this.sun * 40 > this.power) {
                    this.alarm = "肾能量不足";
                } else {
                    this.$emit('plusSun', this.sun);
                    this.sun = 1;
                    this.alarm = '';
                    this.$emit("closeProp");
                }
            },
        },
    }
</script>

<style scoped>
    .prop {
        background-color: rgba(0, 0, 0, 0.4);
        width: 100%;
        height: 100%;
        position: absolute;
        top: 0;
        z-index: 999;
        text-align: center;
    }
    .close {
        display: none;
    }
    .prop-room {
        width: 95%;
        margin: 180px auto 0px;
        border-radius: 20px 20px;
        background-color: #fff;
        font-size: 12px;
        overflow: hidden;
    }
    .prop-head {
        color: #5aab26;
        position: relative;
    }
    .prop-head span {
        font-size: 20px;
        font-weight: 500;
    }
    .prop-body {
        width: 100%;
        height: 100%;
        background-color: #ddd;
        border-radius: 0 0 20px 20px;
    }
    .close-button {
        font-size: 20px;
        line-height: 20px;
        width: 20px;
        height: 20px;
        margin: 10px;
        border: 2px #5aab26 solid;
        border-radius: 50% 50%;
        position: absolute;
        right: 0px;
        top: 0px;
    }
    hr {
        margin: 5px auto 0;
        width: 15%;
        border: 2px #5aab26 solid;
        position: relative;
        top: 2px;
    }
    .alarm {
        height: 12px;
        font-size: 12px;
        color: red;
    }
    .item {
        width: 28%;
        margin: 5px calc(7% / 6);
        border-radius: 5px 5px;
        background-color: #fff;
        display: inline-block;
    }
    .item span {
        color: #000;
        font-size: 18px;
        display: inline;
    }
    .illustrate {
        color: #5aab26;
        font-size: 12px;
        border: #5aab26 solid 1px;
    }
    img {
        width: 60%;
    }
    .add {
        color: #5aab26;
        font-size: 20px;
        padding: 0px 0px 5px;
    }
    .add i{
        padding: 0px 5px;
    }
    .submit {
        background-color: #5aab26;
        padding: 5px;
        font-size: 12px;
        color: #fff;
        border-radius: 0 0 5px 5px;
    }
    .submit span{
        font-size: 15px;
        color: #fff;
    }
</style>