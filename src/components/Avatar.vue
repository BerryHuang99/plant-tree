<template>
    <div class="avatar">
        <img src="../assets/avatar.png">
        <div class="resume">
            <div class="name">
                {{user.name}}
            </div>
            <div class="level">
                {{user.level}}
            </div>
        </div>
        <div class="dialog">
            {{user.weight}}g<span>({{treeName[index]}})</span>>>
        </div>
    </div>
</template>

<script>
    export default {
        props: ['user', 'index', 'treeName'],
        data() {
            return {
            }
        }
    }
</script>

<style scoped>
img {
    height: 60px;
    weight: 60px;
    border: 3px solid #fff;
    border-radius: 50% 50%;
    float: left;
}
.avatar {
    padding: 20px;
}
.resume {
    display: inline-block;
    text-align: center;
    float: left;
    color: #fff;
    margin: 5px 0px 5px 2px;
}
.name {
    font-size: 25px;
    font-weight: 300;
}
.level {
    background-color: #24c7a3;
    font-size: 12px;
    border-radius: 5px;
}
.dialog {
    color: #24c7a3;
    background-image: url("../assets/dialog-1.png");
    background-repeat: no-repeat;
    background-size: 100% 100%;
    display: inline-block;
    padding-left: 30px;
    margin: 20px 0;
    width: 110px;
    height: 35px;
    float: right;
    font-size: 11px;
    line-height: 35px;
}
span {
    margin: 0 2px;
}
</style>