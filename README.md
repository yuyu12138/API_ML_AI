## 项目名称：游说YouShuo
> #### 我的私人导游（旅游解说团）

## 所有者
> #### **梁钰语**

## 产品定位
>  #### 一款旅游景点解说app，主要运用语音合成和和地图搜索POI等人工智能的API，帮助喜欢自由行的用户在景区旅游的时候提供景点解说功能，充当云导游的角色，让用户的旅程充满有趣的知识和故事。

## 核心价值
>  #### 游说app以语音合成为基础功能，应用于移动旅游景点解说场景，用户可以通过点击对应景点的播放互动按钮来收听语音故事

## 目标用户
适用人群 | 旅游行为特点 | 其他
----|----|----
年轻旅游群体 | 大部分会选择自由行/结伴旅游，旅游行程自由度高 | 熟练使用移动app，对旅游景点的地理知识/人文故事感兴趣

 ## 背景故事
 - 国内市面上大部分旅游出行类软件功能都大同小异：提供出行资讯、衣食住行等硬件服务，或者充当旅游行程助手（如携程旅行、马蜂窝旅游、飞猪、爱彼迎等），这类功能的软件市场已经比较饱和，竞争也大。
 - 极少具有人文科普功能的旅游出行类软件。马蜂窝旅游虽然也有对部分景点加以介绍，但因为虽然主打旅游攻略，因此其介绍的内容不深入。
 - 搜索引擎的词条资料介绍过于生硬，不适用于旅游情境，旅游出行者都不会在旅途中主动、零散地搜索/阅读相关景点科普。
 - 所以国内自助导游类/具有旅游解说功能的旅游出行软件在市场上有很大的空白。
 
## 用户痛点
- 去到旅游目的地除了拍照社交网络打卡以外，对当地的旅游景点缺乏认知，也缺少了解的系统渠道
- 搜索引擎的词条资料介绍过于生硬，不适用于旅游情境，游客一般不会在旅途中主动上搜索引擎检索
- 来到陌生的旅游目的地，不知道附近有什么有趣的旅游景区可供即时选择

## 需求列表与人工智能API加值
用户故事 | 重要性 | 备注 | 人工智能API加值
----|----|----|----
 我不想在游览 景点的时候看手机文章，但是同时我也想了解 | 非常重要 | 文章正文具有语音朗读功能，并且能后台播放 | [百度AI_语音技术_语音合成](http://ai.baidu.com/tech/speech/tts)
 到达旅游目的地后，我想了解附近景点的相关开放信息和景点故事| 非常重要 |定位当前位置，点击地图上显示的标记地点查看相关资料 | 1、[高德地图_Web服务_搜索POI](https://lbs.amap.com/api/webservice/guide/api/search/#scene)搜索景区；2、 [高德地图_隐藏地图上的文字标注](https://lbs.amap.com/dev/demo/map-text#Android)和[高德地图_多信息弹窗/气泡效果](https://lbs.amap.com/dev/demo/multiple-infowindows#Android)将应用到景点地图页，显示景区地图全景的时候会标记里面每一个景点，隐藏文字标注，放大地图后会有一个小的信息弹窗，用户可以直接点击语音播放标记播放经典故事，也可以点击弹窗浏览文字内容；3、 [高德地图_地图选点](https://lbs.amap.com/dev/demo/place-choose#Android) [高德地图_地点查询](https://lbs.amap.com/dev/demo/place-search#Android)应用与用户浏览景区地图时查找某个景点的解说语音：用户可以在景区内输入景点关键字搜索，点击返回结果就能在景区定位该景点
 
----- 

## 交互及界面设计
- #### 产品结构思维导图
![image](https://github.com/yuyu12138/API_ML_AI/blob/master/image/youshuolct.png)
- #### 部分API调用流程示意图
1. #### 语音合成API（以语音解说景点为例）
![image](https://github.com/yuyu12138/API_ML_AI/blob/master/image/yuyin.jpg)
#### 2. 地点查询API（以搜索景区地图内景点为例
![image](https://github.com/yuyu12138/API_ML_AI/blob/master/image/chaxun.jpg)

## 产品原型展示
- [首页](https://161013029.github.io/44/#g=1&p=%E9%A6%96%E9%A1%B5)
- [目的地](https://161013029.github.io/44/#g=1&p=%E7%9B%AE%E7%9A%84%E5%9C%B0)
- [目的地_省内检索](https://161013029.github.io/44/#g=1&p=%E7%9C%81%E5%86%85%E6%A3%80%E7%B4%A2)
- [目的地_省内检索_具体景点页面](https://161013029.github.io/44/#g=1&p=%E5%85%B7%E4%BD%93%E6%99%AF%E7%82%B9%E7%95%8C%E9%9D%A2)


## API输出入展示

> ### 测试百度语音合成rest api识别接口流程
### 修改tts.py

从网页中申请的应用获取appKey和appSecret

```python
API_KEY = 'UuKfHCemGimXSX4GTTL2pzlk'

SECRET_KEY = 'hTxooU53kzHEB4TF9Fa9MasWaPpZsupL'
```

### 运行 tts.py，进行合成

命令为tts.py

结果在result.mp3，如果遇见错误，结果在error.txt

其中
```
- Content-Type: audio/mp3，表示合成成功，可以播放MP3 result.mp3
- Content-Type: application/json 表示错误   error.txt打开可以看到错误信息的json
```

### 修改合成参数

```
TEXT = "欢迎使用百度语音";

#发音人选择, 0为普通女声，1为普通男生，3为情感合成-度逍遥，4为情感合成-度丫丫，默认为普通女声
PER = 0;
#语速，取值0-9，默认为5中语速
SDP = 5;
#音调，取值0-9，默认为5中语调
PIT = 5;
#音量，取值0-9，默认为5中音量
VOL = 5;

CUID = "123456PYTHON";

```
> ### 百度语音合成API的Python调用代码
[→ 点击此处查看](https://github.com/yuyu12138/API_ML_AI/blob/master/YouShuo/tts.py)


> ### 高德地点查询(Java)
- ### 配合输入提示功能使用，提升 POI 搜索的用户体验：根据输入提示功能返回的提示词，若提示词的 id  为空，说明该提示词不是 POI，需以该输入词为关键词进行 POI 搜索，查询具体的地点；若 id 不为空，则是真实存在的地点，直接可以在地图上展示。
```
<code class="java hljs"><span class="hljs-meta">@Override</span>
<span class="hljs-function"><span class="hljs-keyword">protected</span> <span class="hljs-keyword">void</span> <span class="hljs-title">onActivityResult</span><span class="hljs-params">(<span class="hljs-keyword">int</span> requestCode, <span class="hljs-keyword">int</span> resultCode, Intent data)</span> </span>{
    <span class="hljs-keyword">super</span>.onActivityResult(requestCode, resultCode, data);
    <span class="hljs-keyword">if</span> (resultCode == RESULT_CODE &amp;&amp; data
        != <span class="hljs-keyword">null</span>) {
        mAMap.clear();
        Tip tip = data.getParcelableExtra(Constants.EXTRA_TIP);
        <span class="hljs-keyword">if</span> (tip.getPoiID() == <span class="hljs-keyword">null</span> || tip.getPoiID().equals(<span class="hljs-string">""</span>)) {
            doSearchQuery(tip.getName());
        } <span class="hljs-keyword">else</span> {
            addTipMarker(tip);
        }
    }
```

> ### 高德地图多信息弹窗/气泡效果(Java)
```
aMap.setOnCameraChangeListener(new AMap.OnCameraChangeListener() {
        @Override
        public void onCameraChange(CameraPosition cameraPosition) {

        }

        @Override
        public void onCameraChangeFinish(CameraPosition cameraPosition) {
            if (!isItemClickAction) {
                locationMarker.setPosition(cameraPosition.target);
            }
        }
    });
```

## API使用比较分析
- ### 百度的语音合成API：
- 语音识别、合成接口调用量无限。QPS识别默认为10，合成为100，可以在百度云控制台申请提高配额
- 语音合成指定某个字的发音：语音合成接口，支持自主标音，通过在所需合成的文字后，增加音标的方式，比如，想把“重音”中的重字，指定合成"chong"的读音时，需将合成文字改为“重（chong2）音”，其中2表示2声，可以根据数字变化调节音调，1对应1声，2对应2声，3对应3声，4对应4声。
- 语音合成目前支持中文普通话播报、中英文混读播报，音色支持男声、女声、度丫丫、度逍遥。
- 不过合成文本长度必须小于1024字节，如果本文长度较长，可以采用多次请求的方式。文本长度不可超过限制。

- ### 高德地图&百度地图

比较内容|百度地图API|高德地图API
---|---|---
是否免费|免费|免费
定位功能|百度智能定位服务帮助广大开发者更好解决"你在哪里这个难题；支持GPS、WiFi、基站融合定位；完美支持各类应用开发者对位罝获取的诉求|高德地图定位通过GPS定位，基站定位，混合定位三种定位模式为用户提供高精度的定位服务，开发者可以通过获取用户位置，设置地理围栏，实现高精度推送，通过用户分布合理布詈资源：实现效益最大化。
地图功能|帮助用户轻松实现全平台地图展示；支持3D高清地图、全景图、实时路况图、静态图；自定义个性化地图样式，打造专属地图；|高德开放平台提供2D, 3D,卫星多种地图形式供开发者选择，无论基于哪种平台，都可以通过高德开放平台提供的API和SDK轻松的完成地图的构建工作。同时我们还提供强大的地图再开发能力，全面的地图数据支持，离线在线两种使用方式，多种地图交互模式，满足各个场景下对地图的需求。
数据服务功能（搜索）|提供位罝描述、地点检索、地址解析、推荐上车点等数据服务；百度&用户隐私地理数据融合，满足个性化数据 使用需求分析；|为用户提供基于地理位罝的搜索功能， 如地点关键宇搜索，周边附近搜索，多边形范围内搜索，地点与坐标点之间 的正逆地理编码搜索，以及搜索输入提示，天气查询等常见搜索功能。|

### 所以从开发角度评估地图API 易用、稳定、效率、业务支持的话：
- 易用性、稳定 高德地图API > 百度地图API
- 业务支持 百度地图API > 高德地图API
- 综合能力高德地图比百度地图专业精准，所以选择使用高德地图API


## 问题
问题（如何让用户了解这个特性） |  结果（沟通已达成的决定）
---|---
用户发现地图上的景点开放信息/景点故事有误 | 用户可以在景区地图界面右上角点击反馈，提交反馈后系统会提醒用户继续享受旅程，并告知用户后台会审核用户的反馈信息
非管辖旅游地/非景区旅游地搜索不到 | 搜索页面显示：未找到含“xxx”的景区/城市
没有国外的旅游景区解说 | 待完善其他国家和地区的旅游景点资料

## 可选方案/产品改版方向
- [ ] 可添加用户旅游足迹的标记
- [ ] 旅游景区的推荐路线
- [ ] 景点观景拍摄点推荐
- [ ] 语音包定制、付费功能
- [ ] 增加社交功能
- [ ] .....
