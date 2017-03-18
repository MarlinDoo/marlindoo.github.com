---
layout: page
title : Get started in 5 steps (API.AI)
header : Post Archive
---

# Get started in 5 steps

[原文地址](https://docs.api.ai/docs/get-started)

- 第一步：创建 Agent
- 第二步：创建 entities
- 第三步：创建 intents
- 第四步：测试、训练你的Agent
- 第五步：集成

-------------------

我们的目标是将创建和集成复杂的会话用户界面的过程尽可能简单。

在本快速入门中，我们将通过一步步指导，让你了解怎样在你的产品中集成API.AI工具，处理自然语言。

## 第一步：创建 agent

一个 API.AI Agent代表了一个你的应用、设备或机器人的会话接口。

在API.AI上注册后，你将收到创建 Agent的提示。如果你已经注册了，参考[这个链接](https://console.api.ai/api-client/#/newAgent)来创建一个新的Agent。

![Get Started Create Agent](http://www.marlindoo.com/assets/images/7a68a45-getting-started-create-agent.png "Get Started Create Agent")

输入新的Agent名字后，选择你的应用通讯使用的语种。目前，API.AI支持15中语言。

> Agent 语种一旦保存，不可修改。当然，如果你希望使用其他语种，可以创建一个新的Agent。

![c47e862-getting-started-select-lang](http://www.marlindoo.com/assets/images/c47e862-getting-started-select-lang.png "Getting Started Select Lang")

为Agent命名并选择语种后，点击“保存”按钮。

或许更多有关Agent细节信息，可以产看[这篇文档](https://docs.api.ai/docs/concept-agents)

##  第二步：创建 entities

创建Agent后，你也许想创建几个entities，从用户的查询中提取必要的信息。API.AI控制台的左区entities面板处，提供了操作入口。

![6932fb3-getting-started-entities](http://www.marlindoo.com/assets/images/6932fb3-getting-started-entities.png "Getting Started Entities")

Entities表示特定用例的概念或对象。需要为用户查询返回JSON响应报文时，Entities被用来存储参数值（以及同义词）。

下面这个披萨快递Agent示例中，entity命名为“type”。它代表用户可以预定披萨的不同类型。一个披萨类型可以有多个名字。所有的名字（同义词）被映射成响应报文中JSON的一个值（除非其他参数值类型被定义）。

![7d35454-getting-started-entity-example](http://www.marlindoo.com/assets/images/7d35454-getting-started-entity-example.png "Getting Started Entity Example")

了解更多关于[Entities](https://docs.api.ai/docs/concept-entities)和[参数](https://docs.api.ai/docs/concept-actions)的信息。


## 第三步：创建intents

创建Entities之后，下一步到Intents面板操作。


An intent determines what kind of user requests should be understood and to what actionable data (JSON response) those requests should be converted.

Below is an example intent from a pizza delivery app, which is designed to understand some basic requests from users when they want to start their order.

![fafb609-Getting-started_intent](http://www.marlindoo.com/assets/images/fafb609-Getting-started_intent.png "Getting Started Intent")


















































