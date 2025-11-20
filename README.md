🚀 Gensyn CodeAssist – Full Installation & Usage Guide

Gensyn CodeAssist is an AI coding assistant that learns from your real-time interactions.
This guide explains installation, login, usage, training workflow, and model updates.

---

1. Required Software (All Platforms)

Python 3.10+

Download:
[https://www.python.org/downloads/](https://www.python.org/downloads/)

Docker

Ubuntu:
[https://docs.docker.com/engine/install/ubuntu/](https://docs.docker.com/engine/install/ubuntu/)

Windows/macOS:
[https://www.docker.com/products/docker-desktop/](https://www.docker.com/products/docker-desktop/)

Curl

Ubuntu install:

```
sudo apt install -y curl
```

General download:
[https://curl.se/download.html](https://curl.se/download.html)

HuggingFace Token

Create token:
[https://huggingface.co/settings/tokens](https://huggingface.co/settings/tokens)

Required permissions:

* Read
* Write

Optional Tools

* VSCode → [https://code.visualstudio.com/download](https://code.visualstudio.com/download)
* build-essential (Linux) → `sudo apt install -y build-essential`

---

2. Full Installation (Ubuntu)

Update system

```
sudo apt update && sudo apt upgrade -y
```

Install Python 3.10+

```
sudo apt install -y python3 python3-venv python3-pip
```

Install Docker

```
sudo apt install -y docker.io
sudo systemctl enable --now docker
sudo usermod -aG docker "$USER"
```

> Restart your terminal after this step.

Verify:

```
docker ps
```

Clone CodeAssist

```
cd ~
git clone https://github.com/gensyn-ai/codeassist.git
cd codeassist
```

Set HuggingFace Token

```
export HF_TOKEN="YOUR_TOKEN_HERE"
```

Start CodeAssist

```
uv run run.py
```

Open in browser:
[http://localhost:3000](http://localhost:3000)

---

3. Restarting CodeAssist

Manual restart

```
cd ~/codeassist
uv run run.py
```

Optional quick alias

```
echo 'alias codeassist="cd ~/codeassist && uv run run.py"' >> ~/.bashrc
source ~/.bashrc
```

Run anytime:

```
codeassist
```

---

4. User Login & Authentication

You can log in using:

* Email (one-time code)
* Google login

Your auth data is saved at:

```
persistent-data/auth/userKeyMap.json
```

---

5. Selecting and Solving Problems

Pick difficulty from the sidebar:

* Easy
* Medium
* Hard

As you type:

* AI writes code directly
* Your edits act as learning signals
* Accept / edit / delete all affect training

---

6. Usage Tips

Pause assistant:

```
Shift + Space
```

Cursor placement matters — keep it close to the area you’re working on.

---

7. Training Logic (How CodeAssist Learns)

CodeAssist logs:

* Your edits
* AI suggestions
* Accept/reject actions
* Final code

To begin training:

```
Ctrl + C
```

---

8. What Happens During Training

* AI actions compared with your edits
* Rewards/penalties calculated
* Model updated
* Saved to:

```
persistent-data/trainer/models/
```

If HF token is valid → model uploads automatically.

---

9. Using Your Updated Model

After training:

1. Restart CodeAssist
2. Updated model loads automatically
3. Continue solving tasks with your personal fine-tuned model

---

10. Points, Rewards & HF Upload Confirmation

After training:

* Check terminal logs
* Check CodeAssist dashboard
* Check your HuggingFace profile

If upload succeeded → points appear automatically.




-


