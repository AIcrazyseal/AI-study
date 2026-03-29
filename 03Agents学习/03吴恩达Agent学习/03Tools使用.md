# LLM使用 tools
> 创建：2026.3.28

LLM工具使用：就是LLM请求调用函数。工具就是我们编码提供给LLM的函数。
**LLM自主决策何时请求调用函数（tools）**，以执行某些操作。
## 一、LLM使用tools的流程
  - 编码实现函数（工具），必须要有函数基本信息的注释（函数功能、函数参数等信息），AISuite开源库代码会自动读取函数注释并告知LLM；
  - 把工具清单提供给LLM，告知其可用的工具清单；
  - LLM根据用户输入的prompt，会从工具清单中自主选择需要调用的工具；
  - LLM会生成函数调用请求，告诉agent需要为LLM调用的函数名字；
  - agent调用函数（此处需要提前人工硬编码）并将该函数输出反馈给LLM，即LLM输入的一部分（prompt）；
  - LLM根据接收的函数输出，生成回答文本，继续执行后续操作。

## 二、LLM自主决策调用函数实现过程
  - AISuite开源库可以实现自动获取工具清单中各个工具（函数）的基本信息（如函数名称、功能描述、参数等）；
  - AISuite开源库可以帮助LLM从工具清单中选择合适的工具；
  - LLM可自主决策生成调用工具的请求；
  - 自动执行函数调用，并将函数结果反馈给LLM。
  实现代码如下：
    ```
      # AISuite是吴恩达团队开发的开源包
      # AISuite开源包能自动获取函数的描述，并生成如下的详细描述函数的Json架构：
      # tools = [{"type":"function",
      #            "function":{"name":"get_***"，
      #                        "description":"定义函数时的函数功能描述……"
      #                        "parameters":{}
      #                        }
      #          }]
      #下面这段代码能自动判断LLM是否需要调用相应的函数，并且自动从tools清单中找到需要调用的函数，并自动执行函数调用、将函数结果反馈给LLM
      #需要注意：aisuite对有些LLM模型接口的实现不能自动完成，需要手动完成

      import aisuite as ai
      client = ai.Client()
      response = client.chat.completions.create(
        model = "deepseek-r:1.5b",
        messages = messages,
        tools = [get_****],  `告知LLM可用工具列表`
        max_turns = 5
      )
    ```
  
## 三、代码执行工具
- 调用Python内置的exec(output)函数，可以让LLM自行编写代码并执行，但这有风险；
- 让LLM编写的代码运行在sandbox沙箱中，能降低数据丢失、敏感信息泄露的风险；
- Docker、E2B可以作为沙箱sandboxe的轻量级方案；
- MCP让开发者更容易得到大量工具，供LLM使用；

## 四、MCP(Model Context Protocol)模型上下文协议
- MCP为LLM获取更多上下文和更多工具；
- MCP提出标准，让应用(client)统一访问服务端（server）的工具tools和数据资源data source;
- MCP client端是相对MCP server而言，就是用户端的应用程序；
- MCP server端是对外提供工具tools和数据资源data source、供MCP Client访问的云端资源；
- dband.ai提供了一个深入讲解MCP的短课程。