<template>
    <div class="tree">
        <img src="../assets/tree.png">
        <div class="dialog">
            种下希望，集树成“森”
        </div>
    </div>
</template>

<script>
    export default {

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
        0% {opacity: 0;}
        20% {opacity: 1;}
        80% {opacity: 1;}
        100% {opacity: 0;}
    }
    .tree {
        text-align: center;
        height: 250px;
        position: relative;
    }
    img {
        height: 250px;
    }
    img:hover {
        animation: shake 2s;
    }
    .dialog {
        background-image: url("../assets/dialog-3.png");
        background-repeat: no-repeat;
        background-size: 100% 100%;
        padding: 10px 10px 20px 10px;
        position: absolute;
        left: 10px;
        top: -20px;
        text-align: center;
        display: inline-block;
        opacity: 0;
    }
    .tree:hover .dialog {
        animation: pop-up 5s;
    }
</style>