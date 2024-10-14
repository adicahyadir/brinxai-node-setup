
---

# BrinX AI Relay & Worker Node Installation Guide

Welcome to the **BrinX AI** Relay and Worker Node setup guide! Follow these simple steps to install and configure your relay or worker node to support the BrinX AI network.

![image](https://github.com/user-attachments/assets/14d02543-5279-415e-9833-8ed87a90c841)

Here’s a README section for "Minimum Requirements":

---

## Minimum Requirements

To ensure optimal performance for running the BrinX AI Node, make sure your system meets the following minimum requirements:

- **CPU**: 8 VCPU Cores
- **Memory**: 16GB RAM
- **Storage**: 300GB SSD
- **GPU**: Optional (Having a GPU can significantly enhance performance and increase earnings)
- **Port**: Port 5011 must be open

---

## Worker Node Setup

Choose between installing via the **Linux GUI** or **Linux CLI**:

- **[Linux GUI Setup](https://brinxai.gitbook.io/brinxai-depin-ai/worker-nodes-setup/worker-nodes-gui-setup-linux)**
- **[Linux CLI Setup](https://brinxai.gitbook.io/brinxai-depin-ai/worker-nodes-setup/worker-nodes-cli-setup)**

### Steps

#### 1. Configure Firewall
```bash
sudo apt-get install -y ufw && sudo ufw allow ssh && sudo ufw allow 5011/tcp && sudo ufw enable && sudo ufw status
```

#### 2. Install Docker (If Not Installed)
```bash
sudo apt install apt-transport-https ca-certificates curl software-properties-common -y
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin -y
```

#### 3. Pull the BrinX AI Worker Node Docker Image
```bash
docker pull admier/brinxai_nodes-worker:latest
```

#### 4. (Optional) Enable GPU Support
If your VPS has a GPU, follow [NVIDIA’s container toolkit installation guide](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html).

#### 5. Run Worker Node Script
```bash
git clone https://github.com/admier1/BrinxAI-Worker-Nodes
cd BrinxAI-Worker-Nodes
chmod +x install_ubuntu.sh
./install_ubuntu.sh
```

#### 6. Monitor Node Logs
To check the status of your node, view the logs:
```bash
sudo docker logs brinxai-worker-nodes-worker-1
```

#### 7. Register Your Worker Node
1. Visit [BrinX AI Worker Registration](https://workers.brinxai.com/register.php?ref=41b1a4ef)
2. Create an account and log in
3. Click **Add Worker Node** and enter your **Node Name** and **IP Address**
4. **Done!** Your worker node is now registered and operational!

---

### Referral Code
Use **ref: 41b1a4ef** during registration for referral benefits.

---

## Relay Node Setup

### Requirements
- **Port:** 1194 (UDP) must be open for communication.

### Steps

#### 1. Configure Firewall
Ensure the required ports are open:
```bash
sudo apt-get install -y ufw && sudo ufw allow ssh && sudo ufw allow 1194/udp && sudo ufw enable && sudo ufw status
```

#### 2. Check CPU Architecture
Determine your architecture to select the correct Docker image:
```bash
uname -m
```
- **x86_64** → AMD64 architecture
- **aarch64** or **arm64** → ARM64 architecture (e.g., Raspberry Pi)

#### 3. Pull the BrinX AI Relay Docker Image
Download the latest BrinX AI relay node Docker image:
```bash
docker pull admier/brinxai_nodes-relay:latest
```

#### 4. Run the Relay Node
Start the relay node based on your architecture:
- **For AMD64**:
  ```bash
  sudo docker run -d --name brinxai_relay --cap-add=NET_ADMIN admier/brinxai_nodes-relay:latest
  ```
- **For ARM64** (Raspberry Pi):
  ```bash
  sudo docker run -d --name brinxai_relay --cap-add=NET_ADMIN admier/brinxai_nodes-relay:arm64
  ```

#### 5. Register Your Relay Node
1. Visit [BrinX AI Relay Registration](https://workers.brinxai.com/register.php?ref=41b1a4ef)
2. Log in and click **Add Relay Node**
3. Enter your node IP address, then click **Add Relay Node**
4. **Done!** Your relay node is now registered and operational!

---

Happy relaying with **BrinX AI**!
