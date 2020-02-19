<template>
  <view> 
      <video  src="{{viedo.videoSrc}}" controls></video>
      <h2>之后再次完善即可，大体就是这样写的页面 ✨</h2>
  </view>
</template>

<script>
export default {
  name: "detail",
  onLoad: function(options) {
    //  console.log(options);获得页面参数
    this.getvideo(options);
  },
  methods: {
    getvideo(options) {
      var that = this;
      uni.request({
        url:
          "https://mockapi.eolinker.com/7b7NMB9c75d613bc39c8f16e4e03a3d4a8f951750079dc5/videoDetail?id=" +
          parseInt(options.id),
        success(res) {
        that.viedo=res.data
        }
      });
    }
  },
  data() {
    return {
      viedo: null
    };
  }
};
</script>

<style scoped lang="less"></style>
