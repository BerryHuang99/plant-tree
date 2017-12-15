<template>
    <div class="tree">
        <img :class="[(index < 8) ? 'shadow-1': 'shadow-2']" src="../assets/shadow.png">
        <img class="tree-img" :src="tree[index]"  @click="click()" :class="{'tree-active': isActive}">
        <div class="dialog" v-text="dialog[index]" :class="[(index < 4)? 'dialog-1': 'dialog-2',{'dialog-active': isActive}]">
        </div>
    </div>
</template>

<script>
    export default {
        props: ['index', 'tree', 'dialog'],
        data() {
            return {
                isActive: false,
            }
        },
        
        methods: {
            click: function () {
                this.isActive = true;
                setTimeout(() => {
                    this.isActive = false;
                }, 3000);
            }
        },
    }
</script>

<style scoped>
    @keyframes shake{
        0% {height: 250px;}
        25% {height: 240px;}
        50% {height: 250px;}
        75% {height: 240px;}
        100% {height: 250px;}
    }
    @keyframes pop-up{
        0% {opacity: 0; z-index:999;}
        20% {opacity: 1;}
        80% {opacity: 1;}
        100% {opacity: 0; z-index:-1;}
    }
    .tree {
        text-align: center;
        margin: 0 auto;
        height: 250px;
        position: absolute;
        bottom: 80px;
        left: 0;
        right: 0;
    }
    .tree-img {
        height: 250px;
        width: 300px;
        position: absolute;
        bottom: 0;
        left: 0;
        right: 0;
        margin: auto;
    }
    .shadow-1 {
        height: 20px;
        width: 100px;
        position: absolute;
        bottom: 20px;
        left: 0;
        right: 0;
        margin: auto;
    }
    .shadow-2 {
        height: 25px;
        width: 180px;
        position: absolute;
        bottom: 20px;
        left: 0;
        right: 0;
        margin: auto;
    }
    .tree-active {
        animation: shake 2s;
    }
    .dialog {
        background-image: url("../assets/dialog-3.png");
        background-repeat: no-repeat;
        background-size: 100% 100%;
        padding: 10px 10px 20px 10px;
        text-align: center;
        display: inline-block;
        opacity: 0;
        z-index: -1;
    }
    .dialog-1 {
        position: relative;
        top: 80px;
        right: 50px;
    }
    .dialog-2 {
        position: absolute;
        left: 20px;
        top: 30px;
    }
    .dialog-active {
        animation: pop-up 3s;
        animation-timing-function: ease-out;
    }
</style>