# LLM使用 tools
> 创建：2026.3.28

LLM工具使用：就是LLM请求调用函数。工具就是我们编码提供给LLM的函数。
**LLM自主决策何时请求调用函数（tools）**，以执行某些操作。
## 一、LLM使用tools流程
- LLM调用工具的流程：
    - 编码实现函数（工具）；
    - 把工具清单提供给LLM，告知其可用的工具清单；
    - LLM根据用户输入的prompt，会从工具清单中自主选择需要调用的工具；
    - LLM会生成函数调用请求，告诉agent需要为LLM调用一个特定的函数；
    - agent调用函数（此处需要提前人工硬编码）并将该函数输出反馈给LLM，即LLM输入的一部分（prompt）；
    - LLM根据接收的函数输出，生成回答文本，继续执行后续操作。

- LLM自主决策调用函数实现过程
  - AISuite开源库可以实现LLM自主决策生成调用工具请求
    ```
      # AISuite是吴恩达团队开发的开源包
      # 下面这段代码能自动把函数的描述，告知LLM
      import aisuite as ai
      client = ai.Client()
      response = client.chat.completions.create(
        model = "deepseek-r:1.5b",
        messages = messages,
        tools = [get_****],  `告知LLM可用工具列表`
        max_turns = 5
      )
    ```
  - agent的System Prompt中会列出LLM可用的工具清单、工具描述（函数名称、函数功能、函数参数等信息）
  - 定义agent函数时，必须要有函数基本信息的注释（函数功能、函数参数等信息），上述AISuite库代码会自动读取函数注释并告知LLM；    

- 代码执行工具
