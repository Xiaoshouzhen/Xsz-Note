## <p align="center">LNTU-MGE整合</p>
<p align="right">--前后端分离；微服务</p>

#### 核心思想
- 以前端为主的分散型服务架构
### 概述
<div style="width:120px;height:2px;background:white;border-radius:5px"></div>

作为一个整合项目，最大的要求即是扩展性，鉴于现阶段最成熟先进的Web开发技术，整合项目提出采用前后端分离的项目结构；
前端使用现今最流行的Vue[version-3.0]框架，配合axios组件，vue-router组件，element-plus组件库等，构建强大的前端部分，通过ajax技术完成前后端的联通；
后端采用微服务架构，通过跨域调用，达成每个项目一个服务，每个服务专人维护，通过前端框架组合到一起的整合结果；
前后端分离架构能够有效解决组内人员技术框架不同，钻研方向不同的问题，快速扩展LNTU-MGE整合项目。
### 前端-Vue框架
<div style="width:120px;height:2px;background:white;border-radius:5px"></div>
Vue框架是LNTU-MGE整合项目人员需要学习的唯一统一技术，旨在解决整合项目可视化功能部分的页面众多，功能复杂，MVC框架难以整合和部署困难问题，简化人员技术负担，只用Vue框架进行前端的编写。

Ajax技术已经成熟，RESTFulApi编写风格逐渐流行，完全可以满足本项目的技术支撑，Vue框架提供了页面编写，Ajax技术支持，组件化等强大的功能，下面进行详细叙述：

#### Vue[version-3.x]框架
##### 页面编写
Vue提供了热加载功能以支持快速修改页面，这是快速编写精美设计页面所必须的，基本的HTML，CSS，JS功能编写功能不再赘述，这是编写页面所必须的技术支撑，Vue还具有大量组件库以支撑局部统一的设计风格和快速的功能实现。

##### Ajax异步数据交换技术
Vue框架支持Axios组件以支持强大的Ajax支撑，通过Axios组件完成Ajax能够完成的所有功能，完成与后端的数据交互。
[Axios官网(中文)](http://www.axios-js.com/)
[Axiso官网(English)](https://axios-http.com/)
[Vue中的Axios教程](https://blog.csdn.net/qq_39765048/article/details/117688019?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522165460871916782184665102%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=165460871916782184665102&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-117688019-null-null.142^v11^pc_search_result_control_group,157^v13^new_style&utm_term=axios&spm=1018.2226.3001.4187)
Axios编写的接口简洁且易于嵌入项目逻辑代码的各部分，实例代码如下：
```js
import axios from "axios";
axios({
		method: 'get',
		url: '/goods.json',
    	params: {
            id:1
        }
	}).then(res=>{
		console.log(res.data);
	},err=>{
		console.log(err);
	})
```
Axios对Ajax技术进行了高度封装，对比JQuery的$.Ajax函数，更加直观和易用，并且完美嵌入Vue中。
##### 组件库
作为强大的前端框架，组件库自然不可或缺，但是只推荐Element-Plus组件库作为统一的局部组件等个控制，减少引入组件，提高项目可控能力，拔高人员技术水平。

#### RESTFULApi风格
作为前后端分离技术的一小部分，其实不必要单独拿出进行叙述，但是为提高对该标准的执行度，单独提出，具体见下链接：
[RESTFUL风格](https://blog.csdn.net/x541211190/article/details/81141459?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522165460919716781483716865%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=165460919716781483716865&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-81141459-null-null.142^v11^pc_search_result_control_group,157^v13^new_style&utm_term=Restful&spm=1018.2226.3001.4187)

### 后端-微服务
微服务在2013年才被提出，短短几年就有这么快速的发展。微服务[架构](https://so.csdn.net/so/search?q=%E6%9E%B6%E6%9E%84&spm=1001.2101.3001.7020)能够实现由小型自主服务组成一个整体应用，各个组成部分之间是松耦合的，复杂性低，各个部分可以独立部署，修复bug或者引入新特性更容易，能够独立扩展，不同技术栈之间可以使用不同框架、不同版本库甚至不同的操作系统平台。
采用微服务框架解决后端问题，微服务是指将系统的功能拆分为多个独立运行的程序进行单独运行，这些程序可以采用不同语言，可以采用不同的数据储存形式，通过与前端的连接即可解决同步开发，语言不同，快速扩展的技术目标。

#### Docker容器技术

Docker是一种容器服务，简单来说就是把程序装到一个一个的箱子里运行而不相互污染，包括程序主体，数据库等。
运用Docker可以有效解决微服务的部署问题，使得其在一台服务器上运行多个功能程序。

#### 注
不采用微服务框架的原因在于会限制语言种类，技术路线过于陡峭。
流行的微服务框架主要是Spring Cloud 和 Dubbo，都对服务进行了或多或少的限制，并且主要加强的是服务器间通信问题，这与本项目的架构不太符合。

### 构建流程与辅助工具选择
#### 1.前端主要页面搭建
主要页面是本项目的重中之重，最为项目整合的主要可视化入口，应具备以下功能：
- 快速扩展
- 统一化风格

推荐自适应布局进行桌面端的编写，而多端页面的升级，则应该使用响应式布局

页面设计首先采用设计工具，这里的辅助工具推荐[即时设计](https://js.design/?source=pz&plan=jssj),设计后进行页面编写能够极大的提升项目搭建效率

#### 2.各功能各自搭建功能页面
面向功能，每部分的实现人员进行该部分的页面设计，注意风格统一，即时设计实现了团队协作和组件风格，能够实现此功能

#### 3.服务打包和各自部署
使用Docker进行服务打包，部署到服务器实现整个流程部署完成

#### 4.维护和升级
由于采用分散式的服务部署，各自升级，各自维护，去中心化

#### 5.辅助工具和功能工具推荐
GitHub：进行有效的项目代码管理
Nginx：前端服务部署
Docker：微服务运行
Pycharm：Python编辑器
IDEA：Java编辑器
Goland：Go语言编辑器
VSc Code/WebStorm：前端编辑器

### 总结

采用以上技术架构完全可以解决本项目的功能实现，达成快速扩展，灵活升级，各自维护的项目目标

计划两年内进行技术普及和基础搭建，后续每级组内人员进行打磨，逐渐完成边出成果边整合的项目升级效率。
