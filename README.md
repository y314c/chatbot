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
- 1. Download Python
-    Visit the Python official website (https://www.python.org/downloads/windows/) download page.
-    Select the latest version (such as Python 3.12.x), and click Download Windows Installer (64-bit/32-bit).
-   Run the installer
- 2. Double-click the downloaded .exe file.
-   Check Add Python to PATH (important! Otherwise, you need to manually configure the environment variables).
-   Click Install Now (default installation) or customize the installation path.
- 3. Verify the installation
-   Open the command prompt (Win + R → enter cmd),
-   Run:
```
python --version
```
-   If the version number is displayed (such as Python 3.12.0), the installation is successful.

<! -- The above modifications were made through 2205308040320-->
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
