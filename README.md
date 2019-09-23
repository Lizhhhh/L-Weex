# L-Weex
开始weex学习,前端真有趣.

# weex 所需的前置环境
 1. node
 2. java
 3. weex-toolkit
 4. android-studio

 # .gitignore
 不让node_modules模块上传到github上(太大了,浪费资源)



# 创建一个weex 项目
 1. weex create weekDemo (回车)
 2. 使用 npm(或cnpm) 安装 package.json里面的依赖.
 3. 手动加入平台:  weex platform add android

# vscode 的热更新
 1. --watch


# weex 项目在浏览器中打开
 1. 找到项目中的 package.json
 2. 找到scripts属性
 3. 找到执行 webpack-dev-server --env.NODE_ENV=development --progress 的自定义指令

# vscode 使用 weex 连接 Android Studio
 1. 安装 vscode-weex (vscode扩展中安装)
 2. 使用 Android Studio 创建一个虚拟的 安卓手机,并打开
 3. 命令行 输入 weex run(回车...)等待几分钟后
 4. weex run(即可在 打开的 Android Studio 中预览weex 项目了)

# 将weex项目在 Android Studio 上显示 (项目的启动)
 1. weex run

# weex 头部组件的创建
 1. 在 src/components 下创建一个 topheader.vue
 2. 根据需求写好topheader.vue 文件
 3. 在 src/index.vue 中导入组件并挂载
 4. 挂载:
    - import topheader from './components/topheader.vue'
    - components: {
          topheader
      }
    - <template>
          <div>
              <topheader></topheader>
          </div>
      </template>


# text 组件
 1. 是weex中用于显示文本的
 2. 如果文本希望超出隐藏,可以使用 lines:1 来实现


# input 组件
 1. input 标签要闭合
 2. input 需要宽度和高度: {height: 80px; width: 750px}

# 导入内置的提醒模块(modal)
 1. const modal = weex.requireModule('modal');
 2. 使用 modal.toast({
   message: 'Hi weex',
   duration: 3
 })

# 内建的 图片 模块的使用
 1. 使用 image 标签,如下
 2. <image class="testImage" src="https://gw.alicdn.com/tfs/TB1yopEdgoQMeJjy1XaXXcSsFXa-640-302.png">
 3. 给图片加宽高, 否则图片无法显示

# 内建list 的下拉加载(loading...)
 1. 首先需要一个 list
 2. 在 list 里面嵌套一个 loading 标签(注:loading 要套在 list 中)
 3. 给 loading 标签绑定 onloading 方法
 4. 给 loading 图标指定 是否显示 :dispaly(hide | show)

# 使用 stream 流获取数据
 1. 导入内建的 stream 模块 const stream = weex.require('stream');


