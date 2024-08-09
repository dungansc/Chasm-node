### Project Information
- Twitter : [@ChasmNetwork](https://x.com/ChasmNetwork)
- Website : [Visit](https://chasm.net)

## Node Info

### Min Requirements

| **Requirement**        | **Details**              |
|------------------------|--------------------------|
| **Operating System**   | Linux (linux/amd64, linux/arm64) |
| **vCPU**               | 1                        |
| **RAM**                | 1GB                       |
| **Disk Space**         | 20GB                     |
| **IP Address**         | Static IP                |


### Recommended Server Requirements

| **Requirement**        | **Details**              |
|------------------------|--------------------------|
| **Operating System**   | Ubuntu (20.04 LTS onwards) |
| **vCPU**               | 2                        |
| **RAM**                | 4GB                      |
| **Disk Space**         | 50GB SSD                 |
| **IP Address**         | Static IP                |

---
### Installation

```bash
sudo apt update && sudo apt upgrade -y
```
### Install Docker
```bash
sudo apt install apt-transport-https ca-certificates curl software-properties-common -y && curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add - && sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable" && sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin -y
```
### Create folder
```bash
mkdir chasm
cd chasm
```
### Setup environment
```bash
nano .env
```
### Copy this format and paste the required value there, you copied earlier from different websites
```bash
PORT=3001
LOGGER_LEVEL=debug

# Chasm
ORCHESTRATOR_URL=https://orchestrator.chasm.net
SCOUT_NAME=NAMASCOUTKAMU
SCOUT_UID=DARIMINTSCOUT
WEBHOOK_API_KEY=your_Webhook_API_Key
# Scout Webhook Url, update based on your server's IP and Port
# e.g. http://123.123.123.123:3001/
WEBHOOK_URL=http://your_VPS_ip:3001/

# Chosen Provider (groq, openai)
PROVIDERS=groq
MODEL=gemma2-9b-it
GROQ_API_KEY=your_Groq_API_Key
```
- Save this file using `Ctrl + X` then `Y` and then press `Enter`
```bash
ufw allow 3001
```
### Start and run Node with Docker
```bash
docker pull johnsonchasm/chasm-scout
docker run -d --restart=always --env-file ./.env -p 3001:3001 --name scout johnsonchasm/chasm-scout
```
```bash
docker logs scout
```
### Check if your node is running successfully
```bash
curl localhost:3001
```
- Done !!
---
### Node Status

- Check your scout status here : [Visit](https://scout.chasm.net/dashboard)
- If you see Yellow or Green, it means your node is working properly, also your yellow dot will be turned into green dot after 1 or 2 hrs
