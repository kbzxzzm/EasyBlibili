<template>
  <view>
    <view class="top">
      <img src="../../../icon/logo2.png" id="ic" />
      <img src="../../../icon/search.png" id="search" />
      <img src="../../../icon/user.png" id="user" />
      <button id="app">下载App</button>
    </view>
    <!-- <Title></Title> -->
    <!-- ../../icon/img_1.jpg -->
    <ul class="nav">
      <li v-for="(item, index) in tablist" :key="index">{{ item }}</li>
    </ul>
    <swiper autoplay indicator-dots circular>
      <swiper-item v-for="(item, index) in swiperlist" :key="index">
        <navigator>
          <image src="{{item.imgSrc}}" mode="widthFix" class="im"></image>
        </navigator>
      </swiper-item>
    </swiper>
    <view class="video">
      <navigator
        url="../detail/index?id={{item.id}}"
        class="video_item"
        v-for="(item, index) in videolist"
        :key="index"
      >
        <div class="img">
          <img src="../../../icon/img_1.jpg" alt="" />
        </div>
      </navigator>
    </view>
  </view>
</template>

<script>
import Title from "../../component/Title";
export default {
  data() {
    return {
      swiperlist: [],
      videolist: [],
      tablist: ["首页", "动画", "番剧", "国创", "音乐"]
    };
  },
  onLoad() {
    this.getswiper();
    this.getvideo();
  },
  methods: {
    getswiper() {
      let that = this;
      uni.request({
        url:
          "https://mockapi.eolinker.com/7b7NMB9c75d613bc39c8f16e4e03a3d4a8f951750079dc5/Swiper",
        success(res) {
          that.swiperlist = res.data.data.swiperList;
        }
      });
    },
    getvideo() {
      let that = this;
      wx.request({
        url:
          "https://mockapi.eolinker.com/7b7NMB9c75d613bc39c8f16e4e03a3d4a8f951750079dc5/videoList",
        success(res) {
          that.videolist = res.data;
        }
      });
    }
  },
  components: {
    Title
  }
};
</script>

<style lang="less">
.c {
  background-color: black;
}
.video {
  width: 100%;
  border-radius: 15rpx;
  border: 1px solid pink;
  background-color: aquamarine;
  image {
    border: 1px solid #ccc;
  }
}

swiper {
  box-sizing: border-box;
  height: 220rpx;
}
.im {
  width: 100%;
  height: 100%;
}
.top {
  display: flex;
  align-items: center;
  padding: 10rpx;
  background-color: white;
}
#ic {
  width: 70px;
  height: 30px;
}
#search {
  flex: 1;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 60rpx;
}
#user {
  width: 10px;
  height: 40px;
  flex: 2;
}
#app {
  flex: 3;
  font-size: 30rpx;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: pink;
  color: #fff;
  border-radius: 10rpx;
  padding: 10rpx;
}
.nav {
  display: flex;
  li {
    flex: 1;
  }
}
</style>
