# 外包项目：转盘随机抽取工作片&&抽查内容
获取本地信息，并通过 Canvas 动态绘制转盘信息

> ##### *因为这是给别人做的一个外包项目，所以放上来的代码是压缩过的阉割版，对完整版源码感兴趣的可以联系我；*

## 一、获取本地信息
通过 Ajax 获取本地配置文件信息
```javascript
$.ajax({ 
    url: "data-settings.xml", 
    success: function (xml){
        // do something
    }
});
```
## 二、初始化转盘和随机抽选模块
根据获取到的配置信息调用如下封装好的接口初始化页面
```javascript
// 初始化转盘模块
$("#village_"+ rotNum +"").AddCanvasTurntable({
    sectorText: xzc_Array[index],
    alertText: xzc_alertText,
    resultTitle: xzc_resultTitle,
    rotateTime: xzc_rotateTime,
    fontSize: ifPhone?12:xzc_fontSize,
    colors: xzc_colors,
    defaultSpacing: ifPhone?20:25
});

//初始化随机抽选模块
$("#content_"+ rotNum +"").AddRandomSelection({
    defaultArray: ccnr_Array,
    defaultLinks: ccnr_LinkArray,
    rollSpeed: ccnr_rollSpeed,
    rollTime: ccnr_rollTime,
    alertText: ccnr_alertText,
    resultTitle: ccnr_resultTitle,
    ifAllowRepeatedSelection: true
});
```

## 三、本地配置文件
```javascript
<?xml version="1.0" encoding="utf-8" ?> 
<datas>
	<!-- 工作片信息设置：Begin -->
	<gongZuoPian name="镇区片">
		<village>
			<value>赤一村</value>
			<value>赤二村</value>
			<value>赤三村</value>
			<value>赤四村</value>
			<value>柏峰村</value>
			<value>乔亭村</value>
			<value>石城村</value>
			<value>后山村</value>
			<value>塘边村</value>
			<value>八石村</value>
			<value>午山干村</value>
			<value>溪西村</value>
			<value>巽村</value>
		</village>
	</gongZuoPian>
	<gongZuoPian name="赤中片">
		<village>
			<value>神坛村</value>
			<value>山盆村</value>
			<value>清溪村</value>
			<value>雅端村</value>
			<value>南杨村</value>
			<value>下水碓村</value>
			<value>上吴村</value>
			<value>新樟村</value>
			<value>鱼曹头村</value>
		</village>
	</gongZuoPian>
	<gongZuoPian name="东朱片">
		<village>
			<value>东朱村</value>
			<value>南青口村</value>
			<value>薛乔村</value>
			<value>双峰村</value>
			<value>雅治街村</value>
			<value>南旺溪村</value>
		</village>
	</gongZuoPian>
	<gongZuoPian name="毛店片">
		<village>
			<value>三角毛店村</value>
			<value>田沿村</value>
			<value>后金宅村</value>
			<value>湾塘村</value>
			<value>五柳村</value>
			<value>三丫塘村</value>
			<value>尚阳村</value>
			<value>前川村</value>
			<value>羊印村</value>
			<value>朱店村</value>
			<value>官余村</value>
			<value>莱山村</value>
			<value>大桥村</value>
			<value>慈溪村</value>
		</village>
	</gongZuoPian> 
	<gongZuoPian name="水岸社区">
		<village>
		</village>
	</gongZuoPian>
	<!-- 工作片信息设置：End -->
	
	<!-- 工作片转盘参数设置：Begin -->
	<gongZuoPian_ZhuanPan>
		<!-- 转盘旋转一次所需的时间，单位 s，默认是 6s -->
		<rotateTime>4</rotateTime>
		<!-- 扇形的字体大小，默认值是 16 -->
		<fontSize>16</fontSize>
		<!-- 全部工作片都被选中之后的弹框内容 -->
		<alertText>所有工作片已全部被抽中！</alertText>
		<!-- 结果框的 title 文本 -->
		<resultTitle>当前已选中的工作片如下：</resultTitle>
		<!-- 插件用到的颜色 -->
		<colors>
			<!-- 扇形颜色一 -->
			<value>#e9536a</value>
			<!-- 扇形颜色二 -->
			<value>#fbd7a1</value>
			<!-- 扇形颜色三：当扇形数为奇数时，最后一块扇形的颜色，如：总共有 5 个工作片，则第五个工作片在转盘上的扇形颜色就用 颜色三 填充，这样就能保证不会跟两边的扇形颜色重合 -->
			<value>#df6679</value>
			<!-- 扇形字体颜色 -->
			<value>#000</value>
			<!-- 指针字体颜色 -->
			<value>#fff</value>
			<!-- 指针和边框颜色 -->
			<value>#666</value>
		</colors>
	</gongZuoPian_ZhuanPan>
	<!-- 工作片转盘参数设置：End -->
	
	<!-- 行政村转盘参数设置：Begin -->
	<xingZhengCun_ZhuanPan>
		<!-- 转盘旋转一次的时间，单位 s，默认是 6s -->
		<rotateTime>4</rotateTime>
		<!-- 扇形的字体大小，默认值是 14 -->
		<fontSize>14</fontSize>
		<!-- 全部行政村都被选中之后的弹框内容 -->
		<alertText>所有行政村已全部被抽中！</alertText>
		<!-- 结果框的 title 文本 -->
		<resultTitle>当前已选中的行政村如下：</resultTitle>
		<!-- 插件用到的颜色 -->
		<colors>
			<!-- 扇形颜色一 -->
			<value>#e9536a</value>
			<!-- 扇形颜色二 -->
			<value>#fbd7a1</value>
			<!-- 扇形颜色三：当扇形数为奇数时，最后一块扇形的颜色，如：总共有 5 个行政村，则第五个行政村在转盘上的扇形颜色就用 颜色三 填充，这样就能保证不会跟两边的扇形颜色重合 -->
			<value>#df6679</value>
			<!-- 扇形字体颜色 -->
			<value>#000</value>
			<!-- 指针字体颜色 -->
			<value>#fff</value>
			<!-- 指针和边框颜色 -->
			<value>#666</value>
		</colors>
	</xingZhengCun_ZhuanPan>
	<!-- 行政村转盘参数设置：End -->
	
	<!-- 抽查内容信息设置：Begin -->
	<chouChaNeiRong>
		<value name="村情">
			<link>./Docs/doc1</link>
		</value>
		<value name="党建基本情况">
			<link>./Docs/doc3</link>
		</value>
		<value name="党员基本情况">
			<link>./Docs/doc2</link>
		</value>
		<value name="应知应会">
			<link>./Docs/doc1</link>
		</value>
		<value name="双星争创创业承诺">
			<link>./Docs/doc2</link>
		</value>
		<!-- 随机跳动的速度，默认为 70(ms); 1s = 1000ms -->
		<rollSpeed>70</rollSpeed>
		<!-- 从点击开始到停止随机跳动的次数，默认为 30 次 -->
		<rollTime>30</rollTime>
		<!-- 全部 抽查内容 都被选中之后的弹框内容 -->
		<alertText>所有抽查内容已全部被选中！</alertText>
		<!-- 结果框的 title 文本 -->
		<resultTitle>当前已选中的抽查内容如下：</resultTitle>
	</chouChaNeiRong>
	<!-- 抽查内容信息设置：End -->		
	
  
	<!-- 科室信息设置：Begin -->	
	<keShi>
		<!-- 科室名称 -->
		<name>党政综合办</name>
		<name>组织线</name>
		<name>宣传线</name>
		<name>统战民宗线</name>
		<name>社会事业服务管理</name>
		<name>社会治安综合治理</name>
		<name>规划建设办</name>
		<name>城乡管理服务办</name>
		<name>（新）农业农村工作办</name>
		<name>（旧）农业农村工作办</name>
		<name>财政财务办</name>
		<name>经济发展服务办</name>
		<name>综合监管中心（网格+安检）</name>
		<name>行政服务中心</name>
		<!-- 转盘旋转一次的时间，单位 s，默认是 6s -->
		<rotateTime>4</rotateTime>
		<!-- 扇形的字体大小，默认值是 16 -->
		<fontSize>16</fontSize>
		<!-- 全部科室都被选中之后的弹框内容 -->
		<alertText>所有科室已全部被抽中！</alertText>
		<!-- 结果框的 title 文本 -->
		<resultTitle>当前已选中的科室如下：</resultTitle>
		<!-- 插件用到的颜色 -->
		<colors>
			<!-- 扇形颜色一 -->
			<value>#e9536a</value>
			<!-- 扇形颜色二 -->
			<value>#fbd7a1</value>
			<!-- 扇形颜色三：当扇形数为奇数时，最后一块扇形的颜色 -->
			<value>#df6679</value>
			<!-- 扇形字体颜色 -->
			<value>#000</value>
			<!-- 指针字体颜色 -->
			<value>#fff</value>
			<!-- 指针和边框颜色 -->
			<value>#666</value>
		</colors>
	</keShi>
	<!-- 科室信息设置：End -->
</datas>
```

## 四、示例
[Demo](https://alvinyw.github.io/Blog/Canvas-Turntable/index.html)
