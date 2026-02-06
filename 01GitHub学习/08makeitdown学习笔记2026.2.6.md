# Makeitdown学习笔记

2026.2.7

**主流大型语言模型经常在不经提示的情况下将 Markdown 融入他们的回答中，这表明他们接受过大量 Markdown 格式文本的训练，并且对其理解非常深入。**
## 一、学习资源

1.[知乎介绍makeitdown](https://zhuanlan.zhihu.com/p/15343421980)

2.[makeitdown官方readme文档](https://github.com/microsoft/markitdown/blob/main/README.md)

## 二、安装使用
1.安装
要安装 MarkItDown，请使用 pip： pip install 'markitdown[all]'。

也可以从源代码安装：\
git clone git@github.com:microsoft/markitdown.git\
cd markitdown\
pip install -e 'packages/markitdown[all]'

'[all]'选项是安装全部支持的格式转换工具，也可以安装部分格式转换工具，例如：\
  pip install 'markitdown[pdf, docx, pptx]'\


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
2.使用\
Command-Line  命令行\
markitdown path-to-file.pdf > document.md

或者用 -o 来指定输出文件：\
markitdown path-to-file.pdf -o document.md

列出已安装的插件：\
markitdown --list-plugins

启用插件请使用：\
markitdown --use-plugins path-to-file.pdf



