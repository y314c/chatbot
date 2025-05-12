# 💬 Chatbot template

A simple Streamlit app that shows how to build a chatbot using OpenAI's GPT-3.5.

[![Open in Streamlit](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://chatbot-template.streamlit.app/)

### How to run it on your own machine

### Installation Guide
﻿
1. **Prerequisites Installation**
- Download all files from the repository and save them in a single folder.
- Open the folder in Visual Studio Code.
- Install either Python 3.12 or Python 3.14.
- (1). Download Python
- &emsp;Visit the Python official website (https://www.python.org/downloads/windows/) download page.
- &emsp;Select the latest version (such as Python 3.12.x), and click Download Windows Installer (64-bit/32-bit).
- &emsp;Run the installer<br>
![images](images/03.png)
- (2). Double-click the downloaded .exe file.
- &emsp;Check Add Python to PATH (important! Otherwise, you need to manually configure the environment variables).<br>
![images](images/04.png)
- &emsp;Click Install Now (default installation) or customize the installation path.
- &emsp;Check the first and fourth options. The first option is to install to all users. The fourth option is to install environment variables.<br>
![images](images/05.png)
- (3). Verify the installation
- &emsp;Open the command prompt (Win + R → enter cmd),Run:
```
python --version
```
- &emsp;If the version number is displayed (such as Python 3.12.0), the installation is successful.

<! -- The above modifications were made through 2205308040320--><br> 

﻿
2. **Environment Configuration**
- Navigate to System Properties → Environment Variables.
- Edit the system PATH variable and add a new entry:
```
[Your Python installation path]\Python\Scripts
```
- Configure Visual Studio Code to use the installed Python interpreter.
﻿
3. **Dependencies Installation**
- Open Command Prompt (Windows+R → type `cmd`).
- Navigate to your project folder and run:
```
pip install -r requirements.txt
```
- *Note: If you encounter download issues, you may need to use alternative network solutions.*

### Running the Application
﻿
1. Launch `streamlit_mapp.py` in Visual Studio Code.
2. Access your chatbot's GitHub repository interface.<br>
![images](images/01.png)
3. Enter your pre-set password to start chatting with the chatbot.<br>
![images](images/02.png)
   
*Note: Service availability may be limited in certain regions.*
<br>
<! -- The above modifications were made through 2205308040301-->
  
### Detailed Function Description and Implementation Analysis of the Module
import streamlit as st
import datetime

def main():
    st.title(" AI Chatbot")
    st.markdown("Simple interactive chat interface")

    if "messages" not in st.session_state:
        st.session_state.messages = []

    with st.sidebar.expander(" Load Context"):
        files = st.file_uploader("Upload files", accept_multiple_files=True)
        if files:
            for file in files:
                file_content = file.getvalue().decode()[:100] + "..."
                st.code(f"{file.name}:\n{file_content}")

    for msg in st.session_state.messages:
        with st.chat_message(msg["role"]):
            st.write(msg["content"])
            st.caption(msg["time"])

    if prompt := st.chat_input():
        current_time = datetime.datetime.now().strftime("%H:%M:%S")
        st.session_state.messages.append({"role": "user", "content": prompt, "time": current_time})
        with st.chat_message("assistant"):
            st.write("Processing...")
            st.session_state.messages.append({"role": "assistant", "content": "Received your message!", "time": current_time})

if __name__ == "__main__":
    main()

