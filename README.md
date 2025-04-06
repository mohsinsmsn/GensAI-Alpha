**💻 Gensyn-ai-Rl-Swarm_Guide {Mac/Linux} 💻**
Device/System Requirements 🖥️


❌❌The Node Wont work on low Specs Devices, It can Cause System Crashing if u try on Low Specs Devices

Signup on Vultr for running FREE VPS Node
https://www.vultr.com/?ref=9744662-9J

Open Your Vps
`ssh username@ip`
Pre-Requirements 🛠
Install Python and Other Tools
For Linux/Wsl
sudo apt update && sudo apt install -y python3 python3-venv python3-pip curl wget screen git lsof

For Mac
brew install python
Check Version

python3 --version
Install Node.js , npm & yarn
For Linux/Wsl
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash - && sudo apt update && sudo apt install -y nodejs
Install Yarn (linux)
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list > /dev/null
sudo apt update && sudo apt install -y yarn
For Mac
brew install node && corepack enable && npm install -g yarn
Check version (Linux/Mac)
node -v
npm -v
yarn -v
👨🏻‍💻 Start The Node (Linux/Mac)
1️⃣ Clone RL-SWARM Repo
git clone https://github.com/gensyn-ai/rl-swarm.git
2️⃣ Create a screen session (vps)
screen -S gensyn
3️⃣ Navigate to rl-swarm
cd rl-swarm
4️⃣ Create & Activate a Virtual Environment
python3 -m venv .venv
source .venv/bin/activate
5️⃣ Install Left-over dependencies
cd modal-login
yarn install
yarn upgrade &&  yarn add next@latest &&  yarn add viem@latest
6️⃣ Run the swarm Node 🚀
cd ..
./run_rl_swarm.sh
After Running the Above command it will promt Would you like to connect to the Testnet? [Y/n] Enter Y

A web Pop-Up will appear, It will ask u to Login ( if no web pop-up then u have to paste this on ur brower http://localhost:3000/

Now Login With Your Email Id, Enter OTP and back to ur Terminal/Wsl? ( VPS users check FAQ1 )

image

Now U can see A ORG_ID On ur Terminal..Save it!
Now It will promt Would you like to push models you train in the RL swarm to the Hugging Face Hub? [y/N] Enter N
image

image

Here we go🚀

Its Done ✅

It will Generate Logs Soon🙌

Detach from screen session (vps)
Use Ctrl + A and then press D

Attach to gensyn Screen to see Logs
screen -r gensyn
🛠 FAQ & Troubleshoot 🛠
1️⃣ How to Login or access http://localhost:3000/ in VPS? 📶
Open a new Terminal and login ur vps

Allow Incoming connection on VPS

sudo apt install ufw -y
sudo ufw allow 3000/tcp
Enable ufw
sudo ufw enable
Install cloudflared on the VPS
wget -q https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb
sudo dpkg -i cloudflared-linux-amd64.deb
Check version
cloudflared --version
Make sure your Node is running on port 3000 in Previous Screen

Run the tunnel command

cloudflared tunnel --url http://localhost:3000
Access the Link from your local machine

image

Now follow Login!

Done!✅

2️⃣ Solution of OOM errors on MacBook (Memory/Cpu limit)
Open -
nano ~/.zshrc
Paste in the file
export PYTORCH_MPS_HIGH_WATERMARK_RATIO=0.0
export PYTORCH_ENABLE_MPS_FALLBACK=1
Reload with
  source ~/.zshrc
3️⃣ How to get the Node Name?
Check the image below to get your Node id!
image

4️⃣ Save your swarm.pem file (for future login)
open a wsl window

If U have to copy this file to your local machine from VPS then Run this command from your local Terminal--

scp USERNAME@YOUR_IP:~/rl-swarm/swarm.pem ~/swarm.pem
It will save here in ur Terminal's Root Directory!

5️⃣ How To start the Next Day (Local Pc)
 cd rl-swarm
 python3 -m venv .venv
source .venv/bin/activate
./run_rl_swarm.sh
Follow official Docs for more info and Errors!

https://github.com/gensyn-ai/rl-swarm/tree/brian-address-cpu-only-crashes?tab=readme-ov-file#troubleshooting
