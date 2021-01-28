# Running a Minecraft Server with Docker on Hetzner

- Hetzner Cloud Console: Add server (e.g. Ubuntu) server with your SSH key
- SSH into server
- Install docker (<https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository>)

  - `curl -fsSL https://get.docker.com -o get-docker.sh`
  - `sudo sh get-docker.sh`

  or

  - `sudo apt-get update`
  - `sudo apt-get instal docker`
  - `sudo apt-get instal docker-compose`
  - `sudo apt-get instal docker.io`

- Make sure docker starts on boot
  - `sudo systemctl enable docker`
- Install Minecraft Bedrock Server (<https://hub.docker.com/r/itzg/minecraft-bedrock-server>)
  - `docker compose up -d` using `docker-compose.yml` or just the commands for docker below.
- Connect to server-IP in Minecraft (Bedrock)
- Done, and now:
  - Keep it running
  - Rescale (power off first)
  - Create snapshot
  - Delete, later recreate from snapshot => works immediately, might have other IP

## Install Without Docker Compose

- `docker volume create mc-volume`
- `docker run -d -it --name mc-server -e EULA=TRUE -p 19132:19132/udp --restart unless-stopped -v mc-volume:/data itzg/minecraft-bedrock-server`

## Referral Link

[Hetzner](https://hetzner.cloud/?ref=jb3lG441Nkdf)
