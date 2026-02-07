# Markitdown学习笔记

2026.2.7

**主流大型语言模型经常在不经提示的情况下将 Markdown 融入他们的回答中，这表明他们接受过大量 Markdown 格式文本的训练，并且对其理解非常深入。**

## 一、学习资源

1.[知乎介绍Markitdown](https://zhuanlan.zhihu.com/p/15343421980)

2.[Markitdown官方文档](https://github.com/microsoft/markitdown)看readme文件即可。

## 二、安装

要安装 MarkItDown，请使用 pip：`pip install markitdown[all]`。

也可以从源代码安装：

```bash
git clone git@github.com:microsoft/markitdown.git
cd markitdown
pip install -e packages/markitdown[all]
```

'[all]'选项是安装全部支持的格式转换工具，也可以安装部分格式转换工具，例如：  pip install 'markitdown[pdf, docx, pptx]'\

* `[all]` Installs all optional dependencies
* `[pptx]` Installs dependencies for PowerPoint files
* `[docx]` Installs dependencies for Word files
* `[xlsx]` Installs dependencies for Excel files
* `[xls]` Installs dependencies for older Excel files
* `[pdf]` Installs dependencies for PDF files
* `[outlook]` Installs dependencies for Outlook messages
* `[az-doc-intel]` Installs dependencies for Azure Document Intelligence
* `[audio-transcription]` Installs dependencies for audio transcription of wav and mp3 files
* `[youtube-transcription]` Installs dependencies for fetching YouTube video transcription

## 三、使用

### 1.命令行工具

* Command-Line  命令行

```bash
  markitdown path-to-file.pdf > document.md
```

* 或者用 -o 来指定输出文件：

```bash
  markitdown path-to-file.pdf -o document.md
```

* 列出已安装的插件：

```bash
  markitdown --list-plugins
```

* 启用插件请使用：

```bash
  markitdown --use-plugins path-to-file.pdf
```

### 2.Markitdown插件

MarkItDown 还支持第三方插件。插件默认被禁用。

* 列出已安装的插件：

```bash
markitdown --list-plugins
```

* 启用插件请使用：

```bash
markitdown --use-plugins path-to-file.pdf
```

* 要查找可用的插件，请在GitHub搜索标签 #markitdown-plugin。
* 要开发插件，请参见 packages/markitdown-sample-plugin 。

### 3.Azure 文档智能

* 使用 Microsoft 文档智能进行转换：
  markitdown path-to-file.pdf -o document.md -d -e "<document_intelligence_endpoint>"
  Foundry Tools中的Azure文档智能是一款基于云的Foundry工具 ，利用机器学习模型从你的文档中提取关键/值对、文本和表格。学习如何在 Azure 门户中创建文档智能资源，详见[这里](https://learn.microsoft.com/en-us/azure/ai-services/document-intelligence/how-to-guides/create-document-intelligence-resource?view=doc-intel-4.0.0)。

### 4.Python API

* Python 的基本使用：

```Python
from markitdown import MarkItDown


md = MarkItDown(enable_plugins=False)  # Set to True to enable plugins
result = md.convert("test.xlsx")
print(result.text_content)
```

* Python 中的文档智能转换：

```python
from markitdown import MarkItDown

md = MarkItDown(docintel_endpoint="<document_intelligence_endpoint>")
result = md.convert("test.pdf")
print(result.text_content)
```

* 要使用大型语言模型进行图像描述（目前仅适用于 pptx 和图像文件），请提供 `llm_client` 和 `llm_model`：

```python
from markitdown import MarkItDown
from openai import OpenAI

client = OpenAI()
md = MarkItDown(llm_client=client, llm_model="gpt-4o", llm_prompt="optional custom prompt")
result = md.convert("example.jpg")
print(result.text_content)
```

### 5.Docker

```sh
docker build -t markitdown:latest .
docker run --rm -i markitdown:latest < ~/your-file.pdf > output.md
```
