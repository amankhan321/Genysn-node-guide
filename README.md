# Genysn-node-guide

Gensyn Node Full Setup Guide (Linux/Mac VPS)


# Login to your VPS

```bash
sudo apt update
```


# Update packages

```bash
sudo apt update && sudo apt install -y python3 python3-venv python3-pip curl wget screen git lsof 
```


# Install Python for (Mac)

```bash
brew install python
python3 --version
```


Check Version

```bash
python3 --version
```


# Install Node.js , npm & yarn

· For Linux/Wsl

```bash
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash - && sudo apt update && sudo apt install -y nodejs
```

· Install Yarn (linux)

```bash
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
```

```bash
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list > /dev/null
```

```bash
sudo apt update && sudo apt install -y yarn
```


· # For Mac

```bash
brew install node && corepack enable && npm install -g yarn
```


# Check version (Linux/Mac)

```bash
node -v
```

```bash
npm -v
```

```bash
npm -v
```

# Start The Node 

```bash
screen -S gensyn
```

```bash
git clone https://github.com/gensyn-ai/rl-swarm.git
cd rl-swarm

python3 -m venv .venv
source .venv/bin/activate

./run_rl_swarm.sh
```

# Now press CTRL+A+D

After that run this cmd's

# Access Dashboard (http://localhost:3000) 

# · Enable Firewall Ports

```bash
sudo apt install ufw -y
sudo ufw allow 22
sudo ufw allow 3000/tcp
sudo ufw enable
```


# Create a Public URL (Cloudflared) run this cmd to get link

```bash
wget -q https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb
sudo dpkg -i cloudflared-linux-amd64.deb

cloudflared tunnel --url http://localhost:3000
```

# here After successful login through gmail otp press Ctrl+C then run this cmd 

```bash
screen -ls
```

Now write this cmd it will show your screen's like below example 


<img width="596" height="143" alt="image" src="https://github.com/user-attachments/assets/4c14fdfb-8896-4812-ad35-521d335e1a9b" />

now write this cmd :

```bash
screen -r gensyn 
```

# Most Important Backup Your Swarm.pem File By Running This Cmd 

```bash
[ -f backup.sh ] && rm backup.sh; \
curl -sSL -O https://raw.githubusercontent.com/zunxbt/gensyn-testnet/main/backup.sh && \
chmod +x backup.sh && ./backup.sh
```


# You will get multiple link after running this cmd , copy first link and paste in your chrome or any other browser it will download automatically



# Most important many users are getting normal error just run this cmd:

❗ Error Fix Command

```bash
deactivate && rm -rf .venv && git stash && git pull && \
python3 -m venv .venv && source .venv/bin/activate && bash run_rl_swarm.sh
```




