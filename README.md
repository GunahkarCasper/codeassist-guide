

Gensyn CodeAssist – Full Installation  Usage Guide (Ubuntu / Windows / macOS)



Gensyn CodeAssist is an AI coding assistant that learns from your interactions in real time.

This guide explains installation, login, usage, training workflow, and model updates.



---



1. Required Software (All Platforms)



The following programs are mandatory for CodeAssist to run:



✅ Python 3.10+



Required to run the backend.

Download → https://www.python.org/downloads/ - https://www.python.org/downloads/



---



✅ Docker



All CodeAssist components run inside Docker containers.



 Ubuntu → https://docs.docker.com/engine/install/ubuntu/](https://docs.docker.com/engine/install/ubuntu/

 Windows/macOS →https://www.docker.com/products/docker-desktop/](https://www.docker.com/products/docker-desktop/



---



✅ Curl



Used for fetching UV and other scripts.

Ubuntu installation:



```bash

sudo apt install -y curl

```



General download → \[https://curl.se/download.html](https://curl.se/download.html)



---



✅ HuggingFace Token



Required for accessing and uploading models.



Create token → https://huggingface.co/settings/tokens](https://huggingface.co/settings/tokens

Give permissions:



✔ Read
✔ Write



---



Optional Tools


VSCode    Code editor   https://code.visualstudio.com/download  -  https://code.visualstudio.com/download  
build-essential (Linux)  Compiler tools  `sudo apt install -y build-essential`                                          



---



2. Full Installation Steps (Ubuntu)



1) Update System



```bash

sudo apt update \&\& sudo apt upgrade -y

```



---



2) Install Python 3.10+



```bash

sudo apt install -y python3 python3-venv python3-pip

```



---



3) Install Docker



```bash

sudo apt install -y docker.io

sudo systemctl enable --now docker

sudo usermod -aG docker "$USER"

```



Important: Restart your terminal after this step.



Verify:



```bash

docker ps

```



---



4) Clone CodeAssist



```bash

cd ~

git clone https://github.com/gensyn-ai/codeassist.git

cd codeassist

```



---



5) Add HuggingFace Token



```bash

export HF\_TOKEN="YOUR\_TOKEN\_HERE"

```



---



6) Start CodeAssist



```bash

uv run run.py

```



Open in browser:

👉 http://localhost:3000](http://localhost:3000



---



3. Restarting CodeAssist



Manual Restart



```bash

cd ~/codeassist

uv run run.py

```



Add Quick Command



```bash

echo 'alias codeassist="cd ~/codeassist \&\& uv run run.py"' >> ~/.bashrc

source ~/.bashrc

```



Launch anytime:



```bash

codeassist

```



---



4. User Login \& Authentication



When CodeAssist launches, a login screen will appear.



You may sign in using:



Email login (one-time code)

Google login



After your first login, your local auth mapping is stored at:



```

persistent-data/auth/userKeyMap.json

```



---



5. Selecting and Solving Problems



Use the left sidebar to choose difficulty:







When you start typing:



The assistant writes code directly into your file
Your edits provide learning signals
Accept, adjust, or delete — all counted during training



---



6. Usage Tips



Pause the Assistant



Press:



```

Shift + Space

```



Cursor Position Matters



AI suggestions depend on cursor location.

Keep it close to the section you are working on.



---



7. Training Logic (How CodeAssist Learns)



While the web UI is open, CodeAssist logs everything:



Your edits
Assistant’s suggestions
Accept/reject actions
Final code solution



To start training:



Return to the terminal where CodeAssist is running and press:



```

Ctrl + C

```



This stops the session and automatically starts model training.



---



8. What Happens During Training



During training, CodeAssist will:



Compare assistant actions vs your final edits
Calculate rewards/penalties
Update your model
Save the new version to:



```

persistent-data/trainer/models/

```



If your HuggingFace token is valid:



Your updated model is uploaded to your HF account automatically



---



9. Using Your Updated Model



After training completes:



1.Restart CodeAssist

2.The newly fine-tuned model loads automatically

3.Continue solving tasks with your personalised assistant



---



10. Points, Rewards \& HF Upload Confirmation



After stopping with Ctrl + C



Check training logs

Check your Gensyn CodeAssist dashboard

Check your HuggingFace profile


If the model uploaded successfully, your points will appear automatically.
