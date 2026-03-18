吴恩达 提示词工程Prompt

> 创建：2026.3.18

## Prompt书写原则

### 原则1 书写清晰、具体的指令

- 策略1：使用分隔符：例如
    - Triple quotes:"""
    - Triple backticks:```
    - Triple dashes:---
    - Angle brackets:< >
    - XML tags: <tag> </tag>
- 策略2：要求结构化输出：例如：Html、Json
- 策略3： Check whether conditions are satisfiedCheck assumptions required to do the task
- 策略4: Few-shot promptingGive successful examples of completing tasksThen ask model to perform the task

### 原则2：指示LLM在问题上花更多的时间仔细思考（这意味LLM会花更多的算力进行思考、推理）
- 指定完成任务的步骤，例如：
  - 第一步：……；
  - 第二步……
  - ……
  - 第N步
- 指示模型在匆忙做出结论前，思考并推理出自己的解决方案

## LLM局限性
- 模型幻觉Hullucination

