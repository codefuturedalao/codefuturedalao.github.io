---
layout:     post                    # 使用的布局（不需要改）
title:      StudyVerilog(一)               # 标题 
subtitle:   《Verilog HDL入门》摘抄笔记					 #副标题
date:       2020-02-01              # 时间
author:     Jackson                      # 作者
header-img: img/verilog-chapter1-bg.jpg    #这篇文章标题背景图片
catalog: true                       # 是否归档
tags:                               #标签
- verilog

---

## # 典型设计流程

```flow
st=>start: 开始
op=>operation: 设计要求说明
op1=>operation: 行为描述
op2=>operation: RTL级描述
op3=>operation: 功能验证和测试
op4=>operation: 逻辑综合/时序验证
op5=>operation: 门级网表
op6=>operation: 逻辑验证和测试
op7=>operation: 版图规划和自动布局布线
op8=>operation: 物理版图
op9=>operation: 版图验证
op10=>operation: 实现
e=>end
st->op->op1->op2->op3->op4->op5->op6->op7->op8->op9->op10->e

​```


```

 Verilog中设计者在每个模块内部可以在4个抽象层次中进行描述

* 行为或算法级
* 数据流级
* 门级
* 开关级



​	在数字电路设计中，术语**寄存器传输级（RTL）描述**在很多情况下时能够被逻辑综合工具接受的行为级和数据流级的混合描述。

（寄存器传输级与行为级区别可见https://blog.csdn.net/a8039974/article/details/43635257)

​	设计者只需要说明数据信息是如何在寄存器之间移动以及如何被处理的，而构成电路的逻辑门极其相互之间的连接数据（资料）由逻辑综合工具自动地从RTL描述中提取出来。

​	可采用三种不同的风格或采用混合风格为设计建模

* 行为风格：用过程化语言结构建模

* 数据流风格：用连续赋值语句建模

* 结构风格：用门和模块的实例引用语句建模

  **Notice：**

  1. **没有定义端口的位数，默认为1位**
  2. **没有声明端口的数据类型，默认为线网**
  3. **连续赋值语句时并发执行的。（assign）**
  4. **所有的intial语句和always语句在0时刻并发执行，只有变量类型能够在这两种语句中赋值**
  5. **always语句具有一个与事件控制（紧跟在@后面的表达式）相关联的顺序快（begin-end），这意味着，无论何时，只要事件发生，顺序快就被执行。在顺序快中的语句按照顺序执行，并且在执行结束后被挂起。顺序过程执行完成后，always语句再次等待事件发生。**
  6. **以$字符开始的标识符被认为系统任务或系统函数，任务可以返回0个或多个值，函数只能返回一个值，函数的执行不需要时间，即不允许有任何延迟，而任务可以带有延迟。**