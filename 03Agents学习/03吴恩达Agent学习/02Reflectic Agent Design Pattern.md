# Reflectic Agent Design Pattern反思型智能体设计模式

> 创建：2026.3.27
> 视频链接：【【吴恩达】2026年公认最好的【Agent智能体】教程！】https://www.bilibili.com/video/BV1DfrdByE2H?p=9&vd_source=f432e53fd4216d9d263cf1d6ef32c226

## Reflection Design pattern
- 反思型agent并不是每次都能100%提升agent输出成果质量
- 有外部反馈信息输入时，反思型agent性能提升更好
- 反思型agent中，生成初稿的LLM和反思初稿的LLM，可以是同一个LLM（两个LLM client的Prompt是不一样的）；也可以是不同的两个LLM，**具有推理能力（又叫思考能力）的LLM在反思型agent中表现更好**
- 提升编写Prompt能力较好的方法是：多看别人编写的优秀Prompt；
- 相较于直接调用LLM、一次性生成结果，Reflectic Agent输出成果质量要好得多。

## 二、图表生成工作流Chart Generation workflow

