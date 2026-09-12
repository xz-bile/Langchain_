	pip常见用法：
	配置镜像源
	pip config set global.index-url            https://pypi.tuna.tsinghua.edu.cn/simple 
	pip config set global.trusted-host pypi.tuna.tsinghua.edu.cn



	安装LangChain的流程：
		1，官网安装anaconda(更全)或者miniconda
		2，配置anaconda的path，在cmd中打开。（或使用anaconda powershell）。
		3，使用conda创建虚拟环境（conda create --name 环境名 python==3.12）太高版本的python容易报错
		4，切换环境(conda activate 环境名)
		5，安装LangChain(pip/conda install langchain=1.2.12)。conda能安装非python包，但更严格。
		
# LanChain概述

## 为什么需要LangChain

	单一大语言模型的局限性：1，知识受限于训练数据（无法获得训练点后的数据）。2，无法直接与外部系统交互（llm无法查询实时数据，调用API或读取数据库）3，不具备状态保持能力（上下文能力差，无法记忆一段对话中某些关键信息）

## LangChain框架的定位

	1，作为中间件连接llm与应用（统一接口对接数据库，搜索引擎，API）
	2，封装复杂逻辑（抽象工具调用，记忆等能力，降低智能体开发难度）
	3，支持智能体协作。多个智能体协同工作，各自完成不同任务（分工合作）。

## LangChain应用场景

![[Pasted image 20260824135328.png]]


## LangChain相关岗位

![[Pasted image 20260824135409.png]]


## LangChainv1.2主要模块

![[Pasted image 20260824135639.png]]

## Langchain四大家族支柱

![[Pasted image 20260824135753.png]]

## AI agent

![[Pasted image 20260824140245.png]]


# 模型的创建与调用

	核心参数：model(指定的模型),api_key(秘钥，官网或得),base_url(看官网开发文档)

## 步骤

	1,配置环境(配置api_key,base_url)。写在.env中
	2,从环境变量读取配置
	3，模型初始化
	4,模型调用

### DEEPSEEK

![[Pasted image 20260826165132.png]]

![[Pasted image 20260826165145.png]]

![[Pasted image 20260826165221.png]]

![[Pasted image 20260826165246.png]]


## 兼容写法（ChatOpenAI）

#### DEEPSEEK
![[Pasted image 20260826165333.png]]

#### 智谱
![[Pasted image 20260826165427.png]]

#### 千问
![[Pasted image 20260826165449.png]]

## 中转平台

#### OpenRouter(需要魔法：可以调用海外大模型)

##### DEEPSEEK
![[Pasted image 20260826165643.png]]


### CloseAI(模型还是通过ChatOpenAI调用，api_key和base_url通过CLOSEAI获得)

#### DEEPSEEK
![[Pasted image 20260826165811.png]]

## 统一接口

![[Pasted image 20260826165931.png]]

### DEEPSEEK
![[Pasted image 20260826170004.png]]

### 阿里百炼
![[Pasted image 20260826170046.png]]

### CLOSEAI

![[Pasted image 20260826170128.png]]

## 小结

### 模型调用方式(DEEPSEEK)
![[Pasted image 20260826170159.png]]

### 参数说明
![[Pasted image 20260826170421.png]]


## 本地部署大模型(ollama下载)


### 常用指令

![[Pasted image 20260827163038.png]]

	官网查看ollama支持的模型


## 模型调用(常用方法及属性)

![[Pasted image 20260829203719.png]]

### invoke

![[Pasted image 20260829204043.png]]

#### 三种输入

##### 文本输入

![[Pasted image 20260829204311.png]]

##### 字典列表

![[Pasted image 20260829204411.png]]

##### 消息对象列表

![[Pasted image 20260829204522.png]]

#### invoke源码

##### 核心内容与基本信息

![[Pasted image 20260829204911.png]]

##### 消耗统计
![[Pasted image 20260829204936.png]]

##### 响应元数据
![[Pasted image 20260829205010.png]]

##### 性能与延迟
![[Pasted image 20260829205057.png]]


##### 工具调用信息
![[Pasted image 20260829205120.png]]

### 流式调用
#### invoke和stream的区别
![[Pasted image 20260829205712.png]]

### 批量调用

#### 一次性接受所有响应
![[Pasted image 20260829205815.png]]
![[Pasted image 20260829205837.png]]

#### 按完成顺序接受响应
![[Pasted image 20260829210007.png]]


### 异步调用
![[Pasted image 20260829210629.png]]

#### ainvoke
	异步调用
#### astream

#### abatch
	异步批处理响应请求
	
### try-Except捕获异常
![[Pasted image 20260829212241.png]]


# LangSmith基本使用（需要Magic）
	LangSmith是langchain生态系统中专门用于LLM应用调试，监控，评估管理的平台。

## 核心应用与开发(功能一)

### 追踪(Tracing)
	追踪：记录每次LLM调用的详细信息
	
![[Pasted image 20260830143447.png]]
### 监控(Monitoring)
	监控：实时查看应用性能

![[Pasted image 20260830143527.png]]

### 数据集与实验

![[Pasted image 20260830143700.png]]
### 评估器
	评估：系统化测试LLM应用

![[Pasted image 20260830143803.png]]

### 标注队列
![[Pasted image 20260830143842.png]]


## 提示词与调试工具(功能二)
### 提示词管理(Prompts)
![[Pasted image 20260830144023.png]]

### 演练场(PlayGround)
![[Pasted image 20260830144117.png]]

### 工作室(Studio)
![[Pasted image 20260830144233.png]]

### 上下文中心
![[Pasted image 20260830144258.png]]


## 部署与沙盒(功能三)

### 部署
![[Pasted image 20260830144348.png]]

### 沙盒
![[Pasted image 20260830144409.png]]

# Messge与提示词模版

## 消息的内部结构

![[Pasted image 20260902100529.png]]

## 消息的类型

### 系统消息

![[Pasted image 20260902100646.png]]

### 用户消息

![[Pasted image 20260902100733.png]]

### 助手(AI)信息
![[Pasted image 20260902100818.png]]


### 工具调用信息
![[Pasted image 20260902100855.png]]

## 消息格式

### Json格式

![[Pasted image 20260902101014.png]]

### 对象格式
![[Pasted image 20260902101051.png]]


## 消息对象字段说明

### SystemMessege参数列表(content可以省略)
![[Pasted image 20260902102912.png]]

### HumanMessege(content可以省略)
![[Pasted image 20260902102954.png]]

	不同初始化的模型对name字段识别也不同。（init_chat_model能够识别不同name提出的问题，ChatOpenRouter就不能识别name字段）

### AIMessege(content可以省略)

![[Pasted image 20260908170542.png]]


### ToolMessege参数列表
![[Pasted image 20260908184735.png]]

### content和content_blocks

#### content
	输入多模态信息时，messeges要用字典列表格式
	
#### content_blocks
![[Pasted image 20260910165208.png]]

## 实战(Messege)

### 流程
![[Pasted image 20260908185448.png]]



