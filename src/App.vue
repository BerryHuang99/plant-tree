<template>
  <div id="app">

    <preload :imgUrlArr="imgUrlArr"/>
    <div class="plant-tree" :class="['bg-' + index]">

      <avatar :user="user" :index="index" :treeName="treeName"/>

      <div class="clearfix"></div>

      <tree :tree="tree" :dialog="dialog" :index="index"/>

      <tool-bar :user="user" :props="props" @openProp="openProp" @addWeight="addWeight"/>

      <div class="clearfix"></div>
    </div>

    <div class="jump">
      <button :class="{'button-active': buttonActive}" @click="clickButton">查看排行榜</button>
    </div>

    <prop :isClose="propClose" :power="user.power" :props="props" @closeProp="closeProp" @plusWater="plusWater" @plusFertilizer="plusFertilizer" @plusSun="plusSun"/>
  </div>
</template>

<script>
import Preload from "./components/Preload"
import Avatar from "./components/Avatar"
import Tree from './components/Tree'
import ToolBar from "./components/ToolBar"
import Prop from './components/Prop'

export default {
  name: 'app',
  created: function() {

    // 在此处申请获取json数据
    // 比如 
    // var jsonData;
    // var request = new XMLHttpRequest();
    // request.open('POST', JSON_FILE, true);
    // request.send();
    // if (request.readyState === 4) {
    //   if (requste.statue === 200) {
    //     jsonDate = request.responseText;
    //   } else {
    //     aletr("发生错误");
    //   }
    // }
    // 将数据传递给json变量
    // var json = JSON.parse(jsonDate);

    var json = {
    "user": {
        "name": "name",
        "level": "透亮会员",
        "weight": 1000,
        "avatar": "static/img/avatar.png",
        "waterTime": 0,
        "fertilizerTime": 0,
        "sunTime": 0,
        "power": 200
    },
    "props": {
        "water": 3,
        "fertilizer": 2,
        "sun": 1,
        "propMax": 5,
        "useMax": 5
    },
    "dialog": [
            "种下希望，集树成“森”",
            "种下希望，集树成“森”",
            "种下希望，集树成“森”",
            "种下希望，集树成“森”",
            "种下希望，集树成“森”",
            "种下希望，集树成“森”",
            "种下希望，集树成“森”",
            "种下希望，集树成“森”",
            "种下希望，集树成“森”",
            "种下希望，集树成“森”",
            "种下希望，集树成“森”"
    ],
    "treeName": [
            "参天大树",
            "参天大树",
            "参天大树",
            "参天大树",
            "参天大树",
            "参天大树",
            "参天大树",
            "参天大树",
            "参天大树",
            "参天大树",
            "参天大树"
    ]
  };

    // 数据传递区
    this.user.name = json.user.name;
    this.user.level = json.user.level;
    this.user.weight = json.user.weight;
    this.user.avatar = json.user.avatar;
    this.user.waterTime = json.user.waterTime;
    this.user.fertilizerTime = json.user.fertilizerTime;
    this.user.sunTime = json.user.sunTime;
    this.user.power = json.user.power;
    this.props.water = json.props.water;
    this.props.fertilizer = json.props.fertilizer;
    this.props.sun = json.props.sun;
    this.props.propMax = json.props.propMax;
    this.props.useMax = json.props.useMax;
    this.dialog = json.dialog;
    this.treeName = json.treeName;
    this.imgUrlArr.push(json.user.avatar);
  },
  components: {
    Preload, Avatar, Tree, ToolBar, Prop,
  },
  // 数据
  data() {
    return {
      user: {
        name: '',
        level: '',
        weight: 0, // 树木重量
        avatar: '',
        waterTime: 0, // 当天浇水次数
        fertilizerTime: 0, // 当天施肥次数
        sunTime: 0, // 当天光照次数
        power: 0, // 肾能量值
      },
      props: {
        water: 0, // 拥有的水滴数目
        fertilizer: 0, //拥有的肥料数量
        sun: 0, // 拥有的阳光数量
        propMax: 0,
        useMax: 0,
      },
      propClose: true,
      buttonActive: false,
      imgUrlArr: [
        '/src/assets/bg_01.png',
        '/src/assets/bg_02.png',
        '/src/assets/bg_03.png',
        '/src/assets/bg_04.png',
        '/src/assets/bg_05.png',
        '/src/assets/bg_06.png',
        '/src/assets/bg_07.png',
        '/src/assets/bg_08.png',
        '/src/assets/bg_09.png',
        '/src/assets/bg_10.png',
        '/src/assets/bg_11.png',
        '/src/assets/dialog-1.png',
        '/src/assets/dialog-2.png',
        '/src/assets/dialog-3.png',
        '/src/assets/fertilizer.png',
        '/src/assets/fertilizing.png',
        '/src/assets/raider.png',
        '/src/assets/shadow.png',
        '/src/assets/shine.png',
        '/src/assets/sun.png',
        '/src/assets/tool.png',
        '/src/assets/watering.png',
        '/src/assets/water.png',
        '/src/assets/tree_low07_00.png',
        '/src/assets/tree_low02_00.png', 
        '/src/assets/tree_low03_00.png', 
        '/src/assets/tree_low04_00.png',
        '/src/assets/tree_low05_00.png',
        '/src/assets/tree_low06_00.png',
        '/src/assets/tree_low07_00.png',
        '/src/assets/tree_low08_00.png',
        '/src/assets/tree_low09_00.png',
        '/src/assets/tree_low10_00.png',
        '/src/assets/tree_low11_00.png'
      ],
      tree: ['/src/assets/tree_low01_00.png',
              '/src/assets/tree_low02_00.png', 
              '/src/assets/tree_low03_00.png', 
              '/src/assets/tree_low04_00.png',
              '/src/assets/tree_low05_00.png',
              '/src/assets/tree_low06_00.png',
              '/src/assets/tree_low07_00.png',
              '/src/assets/tree_low08_00.png',
              '/src/assets/tree_low09_00.png',
              '/src/assets/tree_low10_00.png',
              '/src/assets/tree_low11_00.png'
      ],
      dialog: '',
      treeName: '', 
    }    
  },
  methods: {
    plusWater: function (params) {
      this.props.water += params;
      this.power -= (params * 20);
    },
    plusFertilizer: function (params) {
      this.props.fertilizer += params;
      this.power -= (params * 30);
    },
    plusSun: function (params) {
      this.props.sun += params;
      this.power -= (params * 40);
    },
    openProp: function () {
      this.propClose = false;
    },
    closeProp: function () {
      this.propClose = true;
    },
    clickButton: function () {
      this.buttonActive = true;
      setTimeout(() => {
        this.buttonActive = false;
      }, 1000);
    },
    addWeight: function (params) {
      if (this.user.weight + params < 10000) {
        this.user.weight += params;
      } else {
        this.user.weight = 10000;
      }
      if (params == 20) {
        this.props.water--;
        this.user.waterTime++;
      } else if (params == 30) {
        this.props.fertilizer--;
        this.user.fertilizerTime++;
      } else {
        this.props.sun--;
        this.user.sunTime++;
      }
    }
  },
  computed: { 
      index: function () {
          var index = 0;
          if (this.user.weight < 1001) {
              index =  parseInt((this.user.weight - 1) / 500);
          } else {
              index = parseInt((this.user.weight - 1) / 1000 + 1);
          }
          return index;
      }
  },
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  border: 0;
  outline: none;
}  
#app {
    width: 100%;
    height: 100%;
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    overflow: hidden;
}
.plant-tree {
  background-repeat: no-repeat;
  background-size: 100% 100%;
  width: 100%;
  height: 85%;
  overflow:hidden;
  position: relative;
}
.bg-0 {
  background-image: url('./assets/bg_01.png');
}
.bg-1 {
  background-image: url('./assets/bg_02.png');
}
.bg-2 {
  background-image: url('./assets/bg_03.png');
}
.bg-3 {
  background-image: url('./assets/bg_04.png');
}
.bg-4 {
  background-image: url('./assets/bg_05.png');
}
.bg-5 {
  background-image: url('./assets/bg_06.png');
}
.bg-6 {
  background-image: url('./assets/bg_07.png');
}
.bg-7 {
  background-image: url('./assets/bg_08.png');
}
.bg-8 {
  background-image: url('./assets/bg_09.png');
}
.bg-9 {
  background-image: url('./assets/bg_10.png');
}
.bg-10 {
  background-image: url('./assets/bg_11.png');
}
.clearfix {
  clear: both;
}
.tree {
  margin: 80px 0px 0px;
}
.tool-bar {
      width: 95%;
    margin-left: 2%;
      position: absolute;
    bottom: 7px;
    width: 100%;
}
.jump {
  text-align: center;
  margin: 10px;
}
button {
  font-size: 20px;
  background-image: url("./assets/dialog-2.png");
  background-color: #fff;
  background-repeat: no-repeat;
  background-size: 100% 100%;
  padding: 10px 30px;
}
.button-active {
  padding: 15px 40px;
}
</style>
