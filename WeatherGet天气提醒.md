#介绍
这个小小的东西是因为上学期有几次我没注意看天气预报，没有及时换衣服，感冒了。然后也不想安装一些现成的app提醒自己。干脆自己写一个天气提醒的工具得了。于是，它就开始了。
用中华万年历的天气接口（这个是从某个论坛发现的，不是官方的，官方没有开放这个接口）返回的xml文档，利用dom4j解析这个文档，获取天气信息，这个接口得到的信息还是很多的，有五天的天气预报，包括日间和夜间，海有空气质量以及各种建议，可以[访问这个链接][1]来看详细的文档。并发送邮件或者利用[飞信开放API][2]来发送免费短信给自己和飞信好友。
#项目地址
**[github地址][3]**
**[gitoschina地址][4]**
**[开发日志][5]**
#部分代码说明
##项目树结构
```
├── LICENSE
├── README.md
├── src
│   ├── core
│   │   ├── DownloadXML.java//下载天气xml文档
│   │   ├── GetCurrentTimeOnline.java//获取网络上北京时间，日期
│   │   ├── Home.java//程序入口
│   │   ├── Judge.java//判断天气是否变化过大，需要提醒
│   │   ├── MakeMessage.java//对提取出来的信息进行整合，生成要发送的信息
│   │   ├── ResolveXML.java//解析xml文档
│   │   ├── SendMail.java//发送邮件模块
│   │   └── SendMessage.java//发送短信模块
│   └── datastructure
│       ├── ForecastWeather.java//预报的天气
│       ├── Pollution.java//污染
│       ├── WeatherInfo.java//当日的天气
│       └── Zhishu.java//各种建议
├── temp.xml//下载的xml文档
└── weatherciycode.txt//城市名城和城市代码表

```
##说明
由于这个接口的信息非常详细，导致ResolveXML.java过冗，除了昨天的天气没有处理，其他的信息都解析并保存到了weather里面，而且各项属性的setget都比较完善。weatherinfo的各项参数说明也比较明确。
有关的博文：
>[java利用dom4j解析xml文档][6]
[java 发送邮件][7]
[Linux添加定时任务][8]


[1]: http://wthrcdn.etouch.cn/WeatherApi?citykey=101120101 "天气"
[2]: http://openfetionapi.sinaapp.com/  "飞信开放API"
[3]: https://github.com/Findxiaoxun/WeatherGet "WeatherGet"
[4]: https://git.oschina.net/findspace/WeatherGet "WeatherGet"
[5]: https://git.oschina.net/findspace/WeatherGet/blob/master/dev.md "开发日志"
[6]: http://www.findspace.name/easycoding/1073 "Dom4j"
[7]: http://www.findspace.name/easycoding/907 "Java Mail"
[8]: http://www.findspace.name/res/902 "Cron"