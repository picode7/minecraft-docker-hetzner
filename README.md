# Running a Minecraft Server with Docker on Hetzner

- Hetzner Cloud Console: Add server (e.g. Ubuntu) server with your SSH key
- SSH into server
- Install docker (<https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository>)
  - `curl -fsSL https://get.docker.com -o get-docker.sh`
  - `sudo sh get-docker.sh`
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
