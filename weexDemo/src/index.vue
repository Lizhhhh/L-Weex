<template>
  <div>
    <!-- 头部组件 -->
    <!-- <topheader></topheader> -->

    <!-- 输入框 -->
    <!-- <input
      class="testInput"
      :autofocus=true
      type="text"
      placeholder="请输入您的姓名"
    /> -->

    <!-- 图片 -->
    <!-- <image
      class="testImage"
      src="https://ss1.bdstatic.com/5eN1bjq8AAUYm2zgoY3K/r/www/cache/static/protocol/https/home/img/qrcode/zbios_09b6296.png"
    ></image> -->

    <!-- 文本 -->
    <!-- <text class="greeting">栗子</text> -->

    <!-- 视频 -->
    <!-- <video
      class="video"
      :src="src"
      autoplay
      controls
      @start="onstart"
      @pause="onpause"
      @finish="onfinish"
      @fail="onfail"
    ></video> -->

    <!-- 列表 -->

    <list>

      <!-- 上拉刷新 -->
      <!-- <refresh
        class="refresh"
        @refresh="onrefresh"
        @pullingdown="onpullingdown"
        :display="refreshShow"
      >
        <text class="inicator">Refreshing...</text>
      </refresh> -->
      <!-- <cell v-for="news in lists">
        <div class="panel">
          <text class='list_text'></text>
          <text class="list_content"></text>
        </div>
      </cell> -->
      <!-- 下拉加载 -->
      <!-- <loading
        class="loading"
        @loading="onloading"
        :display="showLoading"
      >
        <text class="inicator">Loading...</text>
      </loading> -->
    </list>

  </div>
</template>

<script>
import topheader from './components/topheader.vue';
const stream = weex.require('stream');

const modal = weex.requireModule('modal');
export default {
  name: 'App',
  components: {
    topheader
  },
  data() {
    return {
      lists: [1, 2, 3, 4, 5],
      showLoading: 'hide',
      refreshShow: 'hide',
      src: 'http://flv2.bn.netease.com/videolib3/1611/01/XGqSL5981/SD/XGqSL5981-mobile.mp4',
      logo: 'https://gw.alicdn.com/tfs/TB1yopEdgoQMeJjy1XaXXcSsFXa-640-302.png'
    }
  },
  methods: {
    onstart(event) {
      this.state = 'onstart'
    },
    onpause(event) {
      this.state = 'onpause'
    },
    onfinish(event) {
      this.state = 'onfinish'
    },
    onfail(event) {
      this.state = 'onfinish'
    },
    // 下拉加载
    onloading(event) {
      this.showLoading = 'show';
      setTimeout(() => {
        const length = this.lists.length;
        for (let i = length; i < length + 4; i++) {
          this.lists.push(i + 1);
        }
        this.showLoading = 'hide';
      }, 1.5 * 1000);
    },
    // 上拉更新
    onrefresh(event) {
      this.refreshShow = 'show';
      setTimeout(() => {
        this.lists = [1, 2, 3, 4, 5];
        this.refreshShow = 'hide';
      }, 2 * 1000);
    },
    // 获取数据
    getNews(url, callback) {
      return stream.fetch({
        method: 'GET',
        type: 'json',
        url: url,
      }, callback)
    }
  },
  created() {
    // 加载成功弹出 'Hi weex'
    modal.toast({
      message: 'Hi weex',
      duration: 3
    });

    // const url = "http://localhost:3000/newsInfo"
    // this.getNews(url, res => {
    //   modal.toast({
    //     message: `数据请求成功 ${res.data}`,
    //     duration: 1
    //   });
    //   this.lists = res.data
    // })
  }
}
</script>
<style scoped>
.inicator {
  font-size: 42px;
  text-align: center;
}
.testInput {
  height: 80px;
  padding: 10px;
  font-size: 32px;
  width: 750px;
  border-bottom-width: 1px;
}
.testImage {
  height: 400px;
  padding: 10px;
  width: 720px;
}

.video {
  widows: 630px;
  height: 350px;
  margin-top: 60px;
  margin-left: 50px;
}
.info {
  margin-top: 40px;
  font-size: 40px;
  text-align: center;
}

.logo {
  width: 424px;
  height: 200px;
}
.greeting {
  font-size: 30px;
}
.message {
  margin: 30px;
  font-size: 32px;
  color: #727272;
}

.panel {
  width: 600px;
  height: 250px;
  margin-left: 75px;
  margin-top: 35px;
  margin-bottom: 35px;
  flex-direction: column;
  justify-content: center;
  border-width: 2px;
  border-style: solid;
  border-color: rgb(162, 217, 192);
  background-color: rgba(162, 217, 192, 0.2);
}
.text {
  font-size: 50px;
  text-align: center;
  color: #41b883;
}
</style>
