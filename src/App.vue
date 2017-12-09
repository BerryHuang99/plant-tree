<template>
  <div id="app">
    <div class="plant-tree">
      <avatar/>
      <div class="clearfix"></div>
      <tree/>
      <tool-bar/>
      <div class="clearfix"></div>
    </div>

    <div class="jump">
      <button>查看排行榜</button>
    </div>
  </div>
</template>

<script>
import Avatar from "./components/Avatar"
import Tree from './components/Tree'
import ToolBar from "./components/ToolBar";

export default {
  name: 'app',
  components: {
    Avatar, Tree, ToolBar
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  border: 0;
  outline: none;
}  
.plant-tree {
  background-image: url('./assets/bg.png');
  background-repeat: no-repeat;
  background-size: 100% 100%;
  width: 100%;
  height: 550px;
}
.clearfix {
  clear: both;
}
.tree {
  margin: 80px 0px 0px;
}
.tool-bar {
  margin: 20px;
}
.jump {
  text-align: center;
  margin: 30px;
}
button {
  font-size: 20px;
  background-image: url("./assets/dialog-2.png");
  background-color: #fff;
  background-repeat: no-repeat;
  background-size: 100% 100%;
  padding: 10px 30px;
}
button:hover {
  padding: 12px 35px;
}
</style>
