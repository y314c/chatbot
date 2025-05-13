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
<！--by覃化杰 -->

安全认证模块
动态 API 密钥输入逻辑 openai_api_key = st.text_input（“OpenAI API 密钥”， type=“password”）
实现逻辑：

将 input type 设置为 “password” 以隐藏纯文本。

未输入键时显示指南提示信息（图标 + 文本组合）。

建议使用 secrets.to 将密钥存储在生产环境中。

安全功能： API Key 动态输入：用户可以通过界面动态输入 API Key。

密钥加密存储：密钥不应以纯文本形式存储。它们应以加密形式存储以增强安全性。

按键显示和隐藏：输入时，应隐藏按键内容，以防止他人。

当用户未输入 key 时，显示引导提示信息，帮助用户完成作。

实现逻辑

API 密钥的动态输入：

import streamlit as st

API 密钥的动态输入逻辑
api_key = st.text_input（“OpenAI API 密钥”， type=“password”）

使用 Streamlit 的功能创建一个密码输入框，用户可以在其中输入他们的 API 密钥。text_input

“type=”password“” 参数确保输入的内容以密文形式显示，从而增强安全性。

密钥加密存储：
建议使用 secrets 模块来存储和管理密钥。secrets 模块是 Python 中的内置模块，专门用于处理敏感信息，例如密码和密钥。

import secrets

Generate an encrypted key
encrypted_api_key = secrets.token_urlsafe(16)

Store the encrypted key (This is just an example. The actual storage method should be determined based on the security requirements of the production environment)
Do not print or expose the key directly in a real scenario
print("Encrypted API Key:", encrypted_api_key)
键隐藏/显示：

已经通过 type=“password” 实现了，输入框中的内容会以密文的形式显示。

键隐藏/显示：

已经通过 type=“password” 实现了，输入框中的内容会以密文的形式显示。

引导提示信息：

当用户尚未输入密钥时，显示指导提示消息和图标。

如果不api_key： st.warning（'请输入您的 OpenAI API 密钥以继续。'） st.image（'path_to_icon.png'） # 替换为图标的实际路径

生产环境

在生产环境中，使用 secrets.to 存储密钥，以保证密钥的安全性和隐私性。

<！--by罗全有 -->



python
Copy Code
# 会话状态初始化与维护
if "messages" not in st.session_state:
    st.session_state.messages = []
‌核心机制‌
利用 Streamlit 的响应式编程特性自动同步状态
消息历史采用列表结构存储角色(content/role)元数据
刷新页面时通过内存持久化保持对话连续性

功能扩展：

持久化存储：
添加JSON文件存储功能，实现浏览器重启后的对话记忆
实现save_conversation()函数用于数据持久化
使用atexit确保脚本终止时数据保存

用户界面元素：
增加文本输入框和发送按钮用于消息编辑
使用Streamlit的st.chat_message实现基础聊天界面布局

消息处理：
创建带角色区分（用户/助手）的消息对象
添加占位符响应生成函数
实现输入验证和字段清理机制

模块化设计：
将不同功能拆分到独立函数（持久化、响应生成）
使用常量定义存储文件路径
为每个功能添加文档注释

可扩展性：
响应生成器可替换为API调用或机器学习模型
存储机制可适配数据库集成
支持扩展多消息属性（时间戳等）

<！--by邓荣祥 -->


# 消息渲染模块的详细功能描述与实现分析

在这款聊天机器人应用中，消息渲染是确保用户与助手之间顺畅且易于理解的沟通的关键部分。有效的消息渲染能够提升用户体验并清晰地传达信息。以下是消息渲染的主要组成部分及其详细说明。

## 代码片段及说明

### 1. 显示现有聊天消息
这段代码从 `st.session_state.messages` 中检索并显示之前的聊天消息，使用户能够回顾他们的对话历史。

```python
for message in st.session_state.messages:
    with st.chat_message(message["role"]):
        st.markdown(message["content"])
```

- **遍历消息**：
  - `for message in st.session_state.messages:` 这行代码遍历存储在会话状态中的所有消息。
  - `st.session_state` 是 Streamlit 提供的一个功能，用于在用户会话中保持数据，确保之前的聊天消息可以被访问。

- **渲染消息**：
  - `with st.chat_message(message["role"]):` 这行代码使用上下文管理器根据消息的角色（可以是“用户”或“助手”）来渲染每条消息。
  - 这种区分有助于在视觉上将消息分开，让用户清楚地知道是谁在说话。

- **显示内容**：
  - `st.markdown(message["content"])` 这行代码使用 Streamlit 的 `st.markdown` 方法来渲染消息内容。
  - 这允许使用基本的 Markdown 格式，使消息更易于阅读且更具吸引力。

### 2. 存储和显示用户输入
当用户提交一条新消息时，将执行以下代码来存储和显示输入：

```python
st.session_state.messages.append({"role": "user", "content": prompt})
with st.chat_message("user"):
    st.markdown(prompt)
```

- **存储用户输入**：
  - `st.session_state.messages.append({"role": "user", "content": prompt})` 这行代码将用户输入（存储在变量 `prompt` 中）添加到 `st.session_state.messages` 列表中。

- **渲染用户消息**：
  - `with st.chat_message("user"):` 这行代码为渲染用户消息创建了一个上下文。
  - 这确保了消息以用户消息的适当格式显示在聊天界面中。

- **显示内容**：
  - `st.markdown(prompt)` 这行代码使用 Streamlit 的 `st.markdown` 方法在聊天窗口中渲染用户输入。
  - 这允许使用基本的 Markdown 格式，使消息更具视觉吸引力且更易于阅读。

### 3. 显示助手回复
助手生成回复后，将使用以下代码：

```python
with st.chat_message("assistant"):
    response = st.write_stream(stream)
```

- **渲染助手消息**：
  - `with st.chat_message("assistant"):` 这行代码为渲染助手的消息创建了一个上下文。
  - 这确保了消息在聊天界面中正确显示，并且以助手角色的适当格式进行格式化。

- **流式响应**：
  - `response = st.write_stream(stream)` 这行代码使用 `st.write_stream` 方法逐步显示助手的回复。
  - 这种方法通过让用户能够实时看到回复的生成过程，而不是等待整个消息一次性出现，从而增强了用户体验，使对话感觉更加动态和自然。
  - 
<！--by黄敏初 -->

# 输入处理模块

在该应用中，输入处理模块负责获取用户的OpenAI API密钥和用户输入的聊天消息。以下是相关代码及详细说明。
## 代码

```python
# Ask user for their OpenAI API key via `st.text_input`.
openai_api_key = st.text_input("OpenAI API Key", type="password")
if not openai_api_key:
    st.info("Please add your OpenAI API key to continue.", icon="🗝️")
else:
    # Create an OpenAI client.
    client = OpenAI(api_key=openai_api_key)

    # Create a session state variable to store the chat messages. This ensures that the
    # messages persist across reruns.
    if "messages" not in st.session_state:
        st.session_state.messages = []

    # Display the existing chat messages via `st.chat_message`.
    for message in st.session_state.messages:
        with st.chat_message(message["role"]):
            st.markdown(message["content"])

    # Create a chat input field to allow the user to enter a message. This will display
    # automatically at the bottom of the page.
    if prompt := st.chat_input("What is up?"):
        # Store and display the current prompt.
        st.session_state.messages.append({"role": "user", "content": prompt})
        with st.chat_message("user"):
            st.markdown(prompt)
```
## 1. 获取OpenAI API密钥:
```
openai_api_key = st.text_input("OpenAI API Key", type="password")
```
- 使用st.text_input创建一个输入框，提示用户输入OpenAI API密钥。type="password"参数确保输入内容以密码形式隐藏显示。
## 2. 验证API密钥有效性:
```
if not openai_api_key:
    st.info("Please add your OpenAI API key to continue.", icon="🗝️")
```
- 如果用户未输入API密钥，使用st.info提示用户需要添加密钥才能继续使用。
## 3. 创建OpenAI客户端:
```
client = OpenAI(api_key=openai_api_key)
```
- 当用户提供有效的API密钥后，使用该密钥创建OpenAI客户端实例，用于后续的API调用。
## 4. 创建聊天输入框:
```
if prompt := st.chat_input("What is up?"):
```
- 使用st.chat_input创建消息输入框，允许用户输入聊天内容。当用户输入消息后，内容会存储在prompt变量中。
## 5. 存储并显示用户输入:
```
st.session_state.messages.append({"role": "user", "content": prompt})
with st.chat_message("user"):
    st.markdown(prompt)
```
- 将用户输入的消息添加到会话状态的messages列表中，并使用st.chat_message显示该消息。

<! -- by 韦统 -->
