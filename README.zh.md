# 💬 聊天机器人模板

一个简单的 Streamlit 应用，展示了如何使用 OpenAI 的 GPT-3.5 构建聊天机器人。

[![在 Streamlit 中打开](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://chatbot-template.streamlit.app/)

### 如何在您自己的机器上运行

### 安装指南

1. **先决条件安装**
- 从代码库下载所有文件并将它们保存在一个文件夹中。
- 在 Visual Studio Code 中打开该文件夹。
- 安装 Python 3.12 或 Python 3.14。
- (1). 下载 Python
- 访问 Python 官方网站 (https://www.python.org/downloads/windows/) 下载页面。
- &emsp;选择最新版本（例如 Python 3.12.x），然后点击“下载 Windows 安装程序（64 位/32 位）”。
- &emsp;运行安装程序<br>
![images](images/03.png)
- (2). 双击下载的 .exe 文件。
- &emsp;勾选“将 Python 添加到 PATH”（重要！否则，您需要手动配置环境变量）。<br>
![images](images/04.png)
- &emsp;点击“立即安装”（默认安装）或自定义安装路径。
- &emsp;勾选第一和第四个选项。第一个选项是安装到所有用户。第四个选项是安装环境变量。<br>
![images](images/05.png)
- (3).验证安装
- &emsp;打开命令提示符（Win + R → 输入 cmd），运行：
```
python --version
```
- &emsp;如果显示版本号（例如 Python 3.12.0），则表示安装成功。

<! -- by 杜俊言 --><br>
2.**环境配置**
-找到到系统属性→ 环境变量。
-编辑系统PATH变量并添加新条目：
```
[您的Python安装路径]\Python\Scripts
```
-配置Visual Studio代码以使用已安装的Python解释器。
﻿
3.**依赖关系安装**
-打开命令提示符（Windows+R→ 键入“cmd”）。
-在命令窗口运行：
```
pip install -r requirements.txt
```
-*注意：如果您遇到下载问题，可能需要使用其他网络解决方案*

###运行应用程序<br>
﻿
1.在Visual Studio代码中启动`streamlit_mapp.py`。<br>

2.访问聊天机器人的GitHub存储库界面。<br>
![images](images/01.png)<br>

3.输入预设密码，开始与聊天机器人聊天。<br>
![images](images/02.png)<br>
   
*注意：某些地区的服务可用性可能有限*
<br>
<！--by杨志勇 -->


## 模块的详细功能描述和实现分析

### 接口初始化和用户指导
· 界面标题和描述：使用st.title（）和st.write（）函数分别显示聊天机器人的标题和描述，并向用户介绍这是一个基于OpenAI GPT-3.5模型的简单聊天机器人，并且需要提供OpenAI API密钥才能使用。
· 获取API密钥：st.text_input（）创建一个安全的文本输入框，要求用户输入OpenAI API密钥，输入内容将以密码形式隐藏，以保护用户密钥的安全性。
### Code demonstration
```import streamlit as st

# Show title and description
st.title("Chatbot")
st.write(
    "This is a simple chatbot that uses OpenAI's GPT-3.5 model to generate responses. "
    "To use this app, you need to provide an OpenAI API key, which you can get [here](https://platform.openai.com/account/api-keys). "
    "You can also learn how to build this app step by step by [following our tutorial](https://docs.streamlit.io/develop/tutorials/llms/build-conversational-apps)."
)
```

### 用户输入验证和界面逻辑
· API密钥验证：通过if not openai_api_key:条件确定用户是否输入了API密钥。如果没有输入，使用st.info（）显示提示，告诉用户需要添加API密钥才能继续。
· 聊天界面占位符：如果用户提供了有效的API密钥，使用pass语句保留位置，表示在用户提供API密钥后，与OpenAI API交互的后续聊天逻辑尚未实现，需要进一步开发。
### Code demonstration
```# Request the user to input the OpenAI API key via a text input box
openai_api_key = st.text_input("OpenAI API Key", type="password")
if not openai_api_key:
    st.info("Please add your OpenAI API key to continue.", icon="")
else:
    # If the API key exists, proceed to display the chat interface
    # This is a placeholder for the subsequent chat logic
    pass
```
