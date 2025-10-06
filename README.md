[合集 - AI工作流实战(11)](https://github.com)

[1.Coze工作流实战：一键生成治愈风格视频06-19](https://github.com/lucky_hu/p/18935982)[2.Coze工作流实战：一键生成像素风格视频06-14](https://github.com/lucky_hu/p/18928909)[3.Coze工作流实战：一键生成鸡汤视频——厉害的人，早已戒掉情绪06-28](https://github.com/lucky_hu/p/18954862)[4.一键生成像素风格视频——咖啡屋的浪漫邂逅07-06](https://github.com/lucky_hu/p/18969060)[5.Coze工作流实战：一键上传excel生成数据图表08-02](https://github.com/lucky_hu/p/19018899)[6.Coze工作流实战：快速搭建网站的智能客服助手08-10](https://github.com/lucky_hu/p/19030448)[7.Coze工作流实战：一键生成历史人物一镜到底爆款短视频08-16](https://github.com/lucky_hu/p/19042674)[8.我的第一个coze 智能体（agent）应用09-07](https://github.com/lucky_hu/p/19077989)[9.coze工作流实战——三分钟读一本名著09-22](https://github.com/lucky_hu/p/19104470)[10.10min搭建一个大模型智能客服助手10-03](https://github.com/lucky_hu/p/19125024)

11.如何把MCP服务集成到智能体？手把手教学(含视频教程)10-05

收起

### 导航

* 前言
* 视频讲解
* 作品展示
* 工作流程展示
* 操作步骤
  + 一 新建mcpserver工作流
  + 二 测试智能体
  + 三 发布智能体
* 结语
* 参考

> AI+ 的时代已经来临，不管你是否愿意，你都必须去接受它。

### 前言

在前面的文章[《10min搭建一个大模型智能客服助手》](https://github.com)中，我们详细介绍了搭建大模型智能客服的详细过程。

但是，这种基于工作流+知识库的模式的方案只能解决通用的问答，还不够""智能""。

所以，我继续增加"难度",对现有工作流进行改造，使其支持[MCP](https://github.com)协议。

这样，更加符合企业的实际业务需要。

自从[MCP](https://github.com)协议发布之后，越来越多的AI厂商开始支持这个协议，如dify、cherrystudio等AI平台。
这将极大推动智能体在企业中的落地和应用。

笔者认为：

* 第一、任何技术的发展都为业务服务的，或者说能更好地推动业务的发展。
  AI技术亦是如此。
* 第二、技术的发展绝对不是跳跃式的，而是建立在前一阶段的基础上的，是一种渐进式的发展。AI技术的发展也是如此。

这就意味着，过去传统的开发积累的技术、文档，一定是可以复用的。 比如，企业多年积累的数据，可以通过AI技术进行赋能，从而实现业务创新。

传统的"堆砌式"UI界面，那些复杂的菜单和按钮，或许会被逐步替代。

对话式的智能体模式将会成为主流，就像微信、钉钉、飞书等IM工具一样，通过对话的方式，实现业务交互。

而，智能体就是对话的载体，MCP就是业务数据和智能体的桥梁，让传统的业务接口，通过对话的方式，实现业务交互。

在前面的系列文章中，笔者已经分享了很多coze工作流的案例集锦。

* [《AI工作流实战合集》](https://github.com)
* [《扣子(coze)工作流实战纪实》](https://github.com)

今天，我们来分享一下在智能体中如何集成我们自定义的MCP服务。

欢迎点赞、收藏、关注。

### 视频讲解

### 作品展示

[![](https://img.zhikestreet.com/2025-10-05_130008_248-min.png)](https://github.com)

### 工作流程展示

[![](https://img.zhikestreet.com/2025-10-05_130402_583-min.png)](https://github.com):[芒果加速器](https://ridecake.org)

### 操作步骤

#### 一 新建mcpserver工作流

##### 1、创建工作流

登录扣子(coze)平台:[https://www.coze.cn/studio](https://github.com)

* 选择"开发平台"->"快速开始"
* 在左侧选择"+",选择"创建应用"，给应用起一个名称，并选择"确认"
* 在左侧资源库页面右上角单击 +资源，并选择工作流。
* 设置工作流的名称与描述，并单击确认。

> 如果没有账户，可以先注册一个，coze空间已经全面开开放，免费使用。

[![](https://img.zhikestreet.com/2025-10-05_130735_135-min.png)](https://github.com)

##### 2、开始节点

开始节点，作为入口。
设置两个变量，一个是"input"，都是字符串类型(String)。

* input：用户输入的问题

> 这里要求必填

[![](https://img.zhikestreet.com/2025-10-05_130954_008.png)](https://github.com)

#### 3、list\_tools节点

该节点是coze官方提供的插件。

通过 SSE 传输方式来发现和调用 MCP 协议工具。详情查看:[https://www.coze.cn/store/plugin/7545011145476931647](https://github.com)

[![](https://img.zhikestreet.com/2025-10-05_131142_017.png)](https://github.com)

#### 4、大模型\_匹配MCP方法

单击知识库检索节点，配置输入下方Query变量参数值为意图识别节点的输出output，然后点击知识库右侧的+按钮，在弹出的选择知识库页面中添加刚刚创建的知识库。

[![](https://img.zhikestreet.com/2025-10-05_131549_246-min.png)](https://github.com)

#### 5、call\_tool节点

[![](https://img.zhikestreet.com/2025-10-05_131838_301.png)](https://github.com)

#### 6、大模型\_总结

[![](https://img.zhikestreet.com/2025-10-05_132038_727-min.png)](https://github.com)

#### 7、结束节点

[![](https://img.zhikestreet.com/2025-10-05_132247_333.png)](https://github.com)

至此工作流搭建完毕。

#### 8、调试

接下来，选择"试运行"，运行后，查看结果。

[![](https://img.zhikestreet.com/2025-10-05_132458_886-min.png)](https://github.com)

### 二 测试智能体

[![](https://img.zhikestreet.com/2025-10-05_132711_903-min.png)](https://github.com)

### 三 发布智能体

[![](https://img.zhikestreet.com/2025-10-05_132940_830.png)](https://github.com)

### 结语

智能客服助手的搭建其实有很多方式，比如使用fastgpt、dify这样的智能体平台也是可以的，但是选择coze是一个非常简便、快捷的方案。

AI工作流适用于解决一些复杂问题。

这对于不会写程序的人来说，是一个可以落地的工具。

2025年，很多企业已经开始推送AI的落地应用，比如构建智能体，构建AI应用等。

MCP的横空出世，将会加速企业AI智能体的落地。

## 参考

* [《Coze官方文档》](https://github.com)
* [《Coze插件商店》](https://github.com)
* [安装并使用 Chat SDK](https://github.com)
* [MCP 简介](https://github.com)

[![](https://img.zhikestreet.com/contact_card-min.png)](https://github.com)
