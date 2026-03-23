吴恩达 提示词工程Prompt

> 创建：2026.3.18

## 一、Prompt书写原则

### 原则1：书写清晰、具体的指令

- 策略1：使用分隔符：例如
  - Triple quotes:"""
  - Triple backticks:```
  - Triple dashes:---
  - Angle brackets:< >
  - XML tags: `<tag>` `</tag>`
- 策略2：要求结构化输出：例如：Html、Json
- 策略3：Check whether conditions are satisfied：Check assumptions required to do the task
- 策略4: Few-shot prompting：Give successful examples of completing tasks，Then ask model to perform the task
  少量训练提示：给出成功完成任务的案例，然后要求模型去完成任务

### 原则2：指示LLM在问题上花更多的时间仔细思考（这意味LLM会花更多的算力进行思考、推理）

- 指定完成任务的步骤，例如：
  - 第一步：……；
  - 第二步……
  - ……
  - 第N步
- 指示模型在匆忙做出结论前，思考并推理出自己的解决方案

### 原则3：迭代提示词Iterative Prompt

不存在一个适合所有场景的Prompt，我们**需要有一个开发适合具体应用的好提示词的过程**，如下：

- 首先构思一个清晰、具体的想法idea，然后实现想法Implementation，获得结果Result；
- 误差分析Error Analysis：找出Prompt工作和不工作的地方，分析结果不达预期的原因;
- 调整想法idea，重新实现想法，得到结果，然后进入下一轮误差分析，循环到完成任务。

## 二、LLM局限性

- 模型幻觉Hullucination
- 减少模型幻觉策略：要求LLM从文本中找出相关的引用，然后要求模型使用这些引用来回答问题或者完成任务。这样通过追溯答案和引用的文档，以减少幻觉。

## 三、Prompt用法
- 1.生成摘要
编写专门的Prompt，从一份或者多份材料中，按以下不同需求生成摘要信息：
  - 生成概括性摘要；
  - **为某个部门或角色，提取有用的摘要信息**。例如：从电子商务网站的用户评论中，提取物流运输评价信息并反馈给物流部门，提取价格评价信息给销售部门，提取物品使用评价信息给售后部门等等。
  - **为某个主题，提取摘要信息**。例如：以网上购物用户评论举例，主题可以是地理区域、天气、重量、时长、好评分4.5以上、差评等等

- 2.推理Inferring
编写Prompt，从分析材料的文字中**提取某方面的内容**，并**推理出结论**，例如：根据用户评论留言，推测用户情绪（愉快、愤怒、不满意等）

- 转换Tansforming