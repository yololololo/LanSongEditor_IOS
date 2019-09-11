#### (当前仓库经过两年的版本迭代,仓库代码已经很大,请直接下载zip包, 不要git clone下载)

## 可能是 唯一 一家提供 图层架构的SDK, 视频编辑, 一层 一层的处理.

*  蓝松短视频编辑SDK, 专业版 ios端演示工程.  
*  每个图层都支持移动 缩放 旋转 滤镜,亮暗,隐藏,等属性; 您可以任意个性化. 比如常见的美颜, 滤镜,文字,涂鸦,MV,增加各种动画, 抖音效果等
*  支持AE模板,你可以直接把设计师做好的视频动画工程,输入到我们SDK中,从而直接实现各种个性化的视频效果.
* . 可做类似微商视频, 小柿饼, 趣制作, 卡点视频, 美册等

 ### 当前版本是3.6.8
- 重新Ae模板合成类,新的名字是LSOAeCompositionView.[全新重大更新]
- LSOAeCompositionView支持极速导出,预览后最快可0.01秒导出.
- LSOAeCompositionView支持暂停恢复,缓冲,渲染进度等功能.
- LSOAeView增加图片路径输入.
- 优化其他代码.


[更多版本日志](https://github.com/LanSoSdk/LanSongEditor_IOS/blob/master/%E7%89%88%E6%9C%AC%E6%9B%B4%E6%96%B0%E8%AE%B0%E5%BD%95.md)

## 架构介绍
![架构示意图](https://github.com/LanSoSdk/LanSoEditor_advance/blob/master/SDK%E6%9E%B6%E6%9E%84%E5%9B%BE%E7%89%87.png)
### 架构1: 图层
*   类似ios中的UI布局, 或者类似 adobe Affect Effect 动画处理一样, 我们的SDK是基于图层架构设计, 所有的素材,都是一层一层的处理;
*   我们设计了一个容器概念, 命名为Drawpad, 向内部增加各种图层, 比如视频图层, 图片图层, mv图层等, 既可完成视频处理;
*   滤镜功能：具有滤镜属性的图层有：视频图层，图片图层，摄像头图层
*   视频图层，可引出多个子图层； 子图层是克隆当前画面， 从而实现同一个画面分裂出多个相同的画面,比如灵魂出窍,模糊背景, 错位等抖音的效果;

### 架构2: AE模板

*   AE模板:  是指设计师用Adobe After Effect做好各种视频动画，比如炫酷视频，文艺/搞笑的场景，相册效果等，根据我们的指导文件导出。蓝松SDK会解析导出的文件,自动还原成AE设计时的动画效果,开发者只需要做的是：引导用户选择素材，然后替换即可,执行后，即可得到用户自己的效果。
*   客户参考：微商水印相机，熊猫动态壁纸,小柿饼等

#### 图层容器操作举例：
*   把给视频增加滤镜： 则你增加视频图层到容器上， 然后调节VideoPen中的滤镜属性即可。
*   再比如： 你要在视频中增加文字： 则你增加[视频图层]+[UI图层]到容器中，在处理过程中，实时的调节他们即可。
*   再比如：你要拍照的同时增加滤镜，或增加图片或视频在四周环绕， 则您可以增加[摄像头图层]+[图片图层]或[视频图层]到容器上，图片设置到四周，视频用滤镜处理成中间透明，就实现您要的效果。
*   再比如：你想生成一段文字或把炫酷的动画转换为视频，则可以直接增加[UI图层]到容器上。
*   再比如：你想给视频实时增加说话声，则可以直接增加[Mic图层]，当然如果仅仅是剪切替换声音，则直接用VideoEditor类中的替换方法就可以。


#### 图层容器 更仅一步说:
* 1，你用 【视频图层 VideoPen】在 容器 DrawPad上作画， 就得到 调整后的视频
* 2，你用 【UI图层  ViewPen】在容器上作画， 就是把精美的UI界面转换为视频， 当然我们的设计，也可以后台处理。
* 3， 你用 【视频图层】+ 【图片图层】 在容器上作画， 就得到动态的视频图片效果。
* 4， 你用  【视频图层】 + 【MV图层】 在容器上作画， 就是在视频中叠加MV的效果。
* 5， 当然： 容器 可以在前台工作， 也可以在后台处理。




### 下载地址: 
*  https://github.com/LanSoSdk/LanSongEditor_IOS

### 我们有android版本的SDK，欢迎你的评估使用：
*	android系统SDK--基本免费版本：https://github.com/LanSoSdk/LanSoEditor_common
*	android系统SDK--专业版本：https://github.com/LanSoSdk/LanSoEditor_advance

### 集成方式
- 1. 拖动LanSongEditorFramework.framework到你的项目中, 并在工程的Build Phases标签页的Link Binary With Libraries中把我们的framework放到最上面.
2. 在Build Phases的<Link Binary With Libraries>中增加libz.tbd , libbz2.tbd, libc++.tbd, libiconv.tbd
3. 在你代码中包括头文件： #import <LanSongEditorFramework/ LanSongEditor.h>
4. LanSongEditorBundle.bundle 是我们sdk中 以LanSongIFxxx开头用到的一些滤镜图片,如果没用到LanSongIFxxx开头的滤镜，则不用增加此文件。如用到则把LanSongEditorBundle.bundle 拖动到你项目的 copy Bundle Resources中
5. **其他的代码，各种资源，各种视频素材等均为演示所用，不属于sdk的一部分。**
6. 如果您选择ios设备中的视频,则应该先拷贝到沙盒里,然后再用我们SDK处理.我们SDK提供了拷贝的方法LSOEditMode. 拷贝后再处理.
7. 代码使用
 ```
初始化
 1.  [LanSongEditor initSDK:nil]//初始化SDK [必须]
 2.  [LanSongEditor setTempFileDir:@"xxx"]; //设置SDK的临时文件路径 [可选]

使用流程[仅参考]:
 1.  明白我们SDK的各种DrawPad/Layer的意思. 我们每个公开类的注释,都在对应的.h头文件里, 您可以简单看下.
 2.  先在我们demo上 运行您要的各种演示功能, 然后拷贝我们的相关demo代码,各种Activity.java, 在您的工程里运行一遍.
 3.  我们每个Activity.java都有注释, 并尽量简单清晰. 您明白大概流程后, 整合归纳成您自己的代码. 
 ```
### 联系方式:
*   QQ 1852600324 
*   Email:support@lansongtech.com
*   网站: www.lansongtech.com
*  如果您下载过慢, 可联系我们, 索取最新的工程包 或向我们索取演示APK安装包.

## 使用案例
*   我们从事的是：商业SDK开发、更新和维护；
*   当前包括500强 大公司在内的大约300+多个上线APP在使用，行业涉及 社交、微商、广场舞、直播、工具、母婴、舞蹈、厨艺、金融、炫酷等多种行业
*   欢迎联系我们，索取相关案例信息和授权说明
