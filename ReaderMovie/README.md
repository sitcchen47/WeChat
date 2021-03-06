# 关于移动端分辨率
  - 将不同尺寸的设计图，按照一定的比例，完美的显示在页面之中
#### pt
  - 逻辑分辨率  
  - 和屏幕的物理尺寸有关
  - 长度和视觉单位
#### px
  - 物理分辨率
  - 不是长度相关的单位
  - 1px就是一个像素点
  - 1 pt物理尺寸下有多像素点（px）
#### Reader
  - 求每一个pt下面包含了多少个px
#### PPI（DPI）
  - 利用分辨率什么的实用勾股定理算出的数值

## 关于rpx--小程序的自适应单位
  - 1个pt可以有一个px构成，也可以有2个，或者更多
  - iPhone6下2个px构成一个pt
#### 如何做不同分辨率设备的自适应
  - 以iPhone6的物理像素750X1135为视觉稿进行设计，在小程序中实用rpx为单位
  - iPhone6 1px = 1rpx = 0.5pt
#### 为什么实用iPhone6的物理分辨率来做设计
  - iPhone6 下 1px = 1rpx
  - iPhone6plus 1px = 0.6rpx
  - 小程序官方推荐使用iPhone6来进行设计
并不是所有的单位都适用rpx




# 开启项目
  - 创建一个纯净的项目模板
  - 配置app.json创建目录
    + wxml是编写小程序的结构文件
    + div是在HTML中书写结构的文件
  - 小程序内的单位rpx
    + rpx与750px设计图是1 ：1的 可以直接实用rpx来实现效果图的样式


## 制作项目启动页面  
  - 使用display: flex;布局，快速完成页面排版
  - 在wxss中书写类名样式，无需在wxml文件中引入，直接添加类名即可实用效果
  - rpx能够适用于各种不同的机型分辨率，强烈建议使用
  - 修改样式，在app.wxss中设置全局样式
  - 设置启动页样式（按照psd设计图还原）
  - 页面默认的容器--pege（类似于html标签）
  - 配置页面导航栏顶端效果（修改json文件中的window配置）

## 使用Swiper组件构建轮播图
  - 修改swiper标签样式调整轮播图
  - 设置image图片大小
  - 自定义轮播整体样式，小点，时间，等

### 修改页面配置文件 .json
  - 因为页面配置文件只能修改window内的样式。所以在页面配置文件内不需要添加windo

## 构建新闻列表
  - 结构分析
  - 使用弹性盒子布局 display：flex
    + 纵向排列 flex-direction: column;
  - 如果控制两个元素的水平间距--》rpx  如果是垂直间距的可以使用px
  - 设置文字和图片的居中 vertical-align: middle;
  - 设置文字间距 letter-spacing: 2rpx;
#### js文件结构与Page页面的生命周期
#### 数据绑定 {{}}
  - 小程序取消了dom节点，及其操作
  - 但是通过{{}} 可以绑定js文件内data对象内声明的变量
  - 小程序内的数据绑定，并不是双向数据绑定的
  - 小程序内需要使用this.setData({}) 对改变的变量重新复制，手动完成双向数据绑定
    + 或直接通过this.data.xxx 找到该属性，进行重新赋值的操作   
  - 使用block标签 包裹要循环的内容
    + block类似与一个括号，将内容包裹起来
  - 使用wx-for 循环创建新闻列表  

 #### 事件绑定
  - 绑定事件 bind || catch
    + 使用wx.navigateTo({}) wx.redirectTo({})方法 改变页面路径，完成跳转
      + wx.navigateTo  保留当前页面，跳转到应用内某个页面，可以返回当前页面
      + wx.redirectTo 关闭当前页面，跳转到应用内某个页面
  - bind    事件绑定不会阻止事件向上冒泡
  - catch   事件绑定可以阻止冒泡事件向上冒泡

#### 使用require 方法加载外部js文件
  - 首先外部js文件需要使用 module.exports 方法导出
  ```javascript
  // ES5
    module.exports = {
      变量名:要导出的内容,
      变量名:要导出的内容
    }
  // ES6
  export default {
    local_database
  };  
  ```
  - 使用require方法 加载需要使用的js文件
  ```javascript
    // ES5
    var post = require(相对路径);
    // 只能使用相对路径
    // ES6
    import postsData from '../data/posts-data.js'
  ```
##### 关于导入外部文件
  - 在进行书写代码时，数据是数据
  - 业务逻辑就是业务逻辑
  - 可以将数据写在单独的文件内，在业务逻辑内引入使用
  - 防止数据内数据冲突过多

#### template模板的使用
  - 创建模板文件
    + 在模板内部书写内容
  - 在需要使用模板的文件内，引入模板 
