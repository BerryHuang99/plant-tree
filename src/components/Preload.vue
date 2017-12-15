<template>
    <div class="load" :class="[loaded? 'disappear': 'appear']">
        <div class="spinner">
            <div class="rect1"></div>
            <div class="rect2"></div>
            <div class="rect3"></div>
            <div class="rect4"></div>
            <div class="rect5"></div>
        </div>
    </div>
</template>

<script>
    export default {
        props: ['imgUrlArr'],
        data() {
            return {
                loaded: false,
                loadNum: 0,
            }
        },
        mounted: function() {
            this.imgUrlArr.forEach((imgUrl, i) => {
                var img = new Image();
                img.addEventListener('load', this.loading);
                img.addEventListener('error', this.loading);
                img.src = imgUrl;
            });
        },
        methods: {
            loading: function () {
                this.loadNum++;
                if (this.loadNum == this.imgUrlArr.length) {
                    this. loaded = true;
                }
            }
        }
    }
</script>

<style scoped>
.load {
    height: 100%;
    width: 100%;
    position: absolute;
    background-color: #fff;
}
.appear {
    z-index: 1000;
    opacity: 1;
}
.spinner {
  margin: 70% auto;
  width: 50px;
  height: 60px;
  text-align: center;
  font-size: 10px;
}
 
.spinner > div {
  background-color: #67CF22;
  height: 100%;
  width: 6px;
  display: inline-block;
   
  -webkit-animation: stretchdelay 1.2s infinite ease-in-out;
  animation: stretchdelay 1.2s infinite ease-in-out;
}
 
.spinner .rect2 {
  -webkit-animation-delay: -1.1s;
  animation-delay: -1.1s;
}
 
.spinner .rect3 {
  -webkit-animation-delay: -1.0s;
  animation-delay: -1.0s;
}
 
.spinner .rect4 {
  -webkit-animation-delay: -0.9s;
  animation-delay: -0.9s;
}
 
.spinner .rect5 {
  -webkit-animation-delay: -0.8s;
  animation-delay: -0.8s;
}

.disappear {
    animation: disappear 0.8s;
    display: none;
}
 
@-webkit-keyframes stretchdelay {
  0%, 40%, 100% { -webkit-transform: scaleY(0.4) } 
  20% { -webkit-transform: scaleY(1.0) }
}
 
@keyframes stretchdelay {
  0%, 40%, 100% {
    transform: scaleY(0.4);
    -webkit-transform: scaleY(0.4);
  }  20% {
    transform: scaleY(1.0);
    -webkit-transform: scaleY(1.0);
  }
}

@keyframes disappear {
    0% {opacity: 1;}
    50% {opacity: 0.5;}
    100% {opacity: 0;}
}
</style>