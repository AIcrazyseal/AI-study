# Equipping agents for the real world with Agent Skills

```
Anthropic发布
20256.2.16
```

**技术思路：通用Agent+Skill（有序的指令skill.md、脚本scripts、references文件、assets模板打包成可组合、专业知识的资源）=垂直领域专用Agent。**
**优势：一个通用Agent、动态发现并渐进式加载不同专业领域的Skill文件夹，完成特定专业领域任务,从而实现完成跨域复杂任务，避免开发定制的专业领域Agent。** 
[Skill文档说明](https://agentskills.io/specification#progressive-disclosure)
![Agent + Skills + Virtual Machine](../../images/Agent+Skills+VirtualMachine.png)

## skill文件夹结构

### 1.典型的skill文件文件夹结构

skill-name/  \
|── SKILL.md               #必须\
    |── YAML frontmatter   #必须 必须包含name、description字段\
    |── Body content       #必须 skill.md的主体正文\
|── scripts/               #可选 包含Agent可执行的代码\
|── references/            #可选 包含Agent在需要时可阅读的参考文件（REFERENCE.md、FORMS.md、域特定文件）\
|── assets/                #可选 包含文档/配置等模板、图片、数据文件等静态资源\
### 2.典型skill文件结构
#### （1）YAML格式的前言
YAWL前言格式要说明这个skill干什么用的，何时调用。\
**name:**  skill-name，只能是数字和字母，开头、结尾不能用“-”，不能包含“--”，例如pdf-processing\
**description:**  描述skill.md的功能，何时使用，例如：
description: Extracts text and tables from PDF files, fills PDF forms, and merges multiple PDFs. 
Use when working with PDF documents or when the user mentions PDFs, forms, or document extraction.\
**license:**  Apache-2.0\
**metadata:** \
  **author:**  example-org\
  **version:**  "1.0"
#### （2）skill.md主体内容
包含skill指令，应逐步说明，并给出输入输出例子，常见的边缘情况。

### 3.skill渐进式披露过程
    * 第一层YAWL元数据（~100个token）：所有技能的名称和描述字段在启动时加载\
    * 第二层skill说明（ 建议<5000给token）：技能激活时，完整 SKILL.md 体被加载\
    * 第三层资源（根据需要）：文件（例如scripts/、references/,、assets/）仅在需要时加载\
![Agent渐进式加载Skill.md](../../images/Agent渐进式加载Skill.md.png)

保持主SKILL.md在 500行以下，将详细参考资料转移到独立文件。\
使用 skills-ref 参考库来验证你的技能,检查你的 SKILL.md 前置内容是否有效，并且符合所有命名规范：
> skills-ref validate ./my-skill
