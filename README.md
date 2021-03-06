# TrackPedometer

## 跑起来

一个跑步时用的轨迹记录和计步器APP

> 初学Android =  一枚小白 + 一只小白应用 

## UI
* 使用了 Fragment碎片化 来分屏展示地图和计步这两个功能
* 计步器界面的合理布局恰当的集成了应有的功能
* 通过不断尝试修改颜色，样式，宽高等各种元素来精心打磨出现在这个界面 简洁友好，柔和舒适 的高大上的UI风格
* Toast的适量友好提示增强了应用交互友好感
* 支持触摸和滑动来切换地图和计步
* 子菜单的设计丰富了应用功能的同时又不过多占用屏幕空间
* 通过曲线展示了感光度的变化以便用户可以及时调整光敏度
* 提供了帮助内容，点击menu键可查看帮助
* 使用了Scrollview，Relativelayout等设计来适应不同屏幕分辨率的手机

## 功能
### 1. 地图
* 使用了GPS传感器和方向传感器，可以后台运行
* 使用了方向传感器来保证地图的朝向于手机朝向一致
* 实现了定位和移动当前位置到屏幕中心点的功能，同时Toast当前地理位置
* 实现了轨迹记录的功能，并且自定义记录的开始和结束，并用显眼的标记标注起点和终点
* 实时监测提醒网络和GPS是否可用
* 子菜单提供了截图保存，清除图层，切换地图三模式，切换普通和卫星地图，快速到达GPS开关设置等功能
* 提供了后台运行功能，防止程序退出后无法记录轨迹
* 利用了自带GPS传感器和百度地图定位API来共同协调定位，由于GPS虽然室外定位精度较高，但搜索卫星速度较慢，开始无法及时定位，而且室内也无法定位，而自带的谷歌网络定位服务在大陆无法使用，此时就需要使用了室内定位和GPS定位结合的方式进行定位的百度地图来辅助定位了。
* 但由于坐标涉及了个人隐私，百度地图坐标在GCJ-02坐标系统上进行了BD-09二次加密，所以要对GPS采集到的坐标映射为百度地图坐标来进行修正。
* 由于采用了GPS传感器定位和百度定位这两种定位方式，在室内或卫星信号弱时主要得到百度网络坐标数据，但在室外和网络信号良好时会得到两个坐标数据，此时若记录轨迹，则假设当前定位到的坐标是正确的，选取距离当前坐标最近的一个点作为下一个点的坐标，同时采取距离权重公式来过滤不合理坐标和补偿早期的定位误差。


### 2. 计步器
* 使用了加速度传感器和亮度传感器，并且分别实现了响应的service，可以真正的后台运行
* 实现了普通模式和口袋模式的计步
* 提供了重置，开始，暂停，继续功能
* 简洁而优雅的步数显示
* 开启计步的同时可以同时开启地图轨迹记录
* 可计算时间，卡路里，路程，均速
* 可触摸对应区域设置目标步数，身高，体重，步长等选项
* 设置的选项和一些相对固定参数已通过sharedpreferences存储，以便下次启动不需要重新设置
* 可自行根据实际情况调整算法灵敏度
* 用简洁的曲线勾画了上20个感光度变化，以供用户正确的调整口袋模式的光敏度
* 人性化的根据用户切换到口袋模式时的环境光照来自动调整光敏度以获得更好的口袋模式效果
* 触摸步数可弹出分享界面，并可自由编辑分享内容

![1](/output/pic.jpg)

![1](/output/1.png)

![1](/output/2.png)

![1](/output/3.png)

![1](/output/4.png)

![1](/output/5.png)

![1](/output/6.png)

![1](/output/7.png)