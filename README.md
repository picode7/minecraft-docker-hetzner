# Running a Minecraft Server with Docker on Hetzner

- Hetzner Cloud Console: Add Server (e.g. ubuntu) server with SSH keys
- SSH into server
- Install docker (https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository)
  - `curl -fsSL https://get.docker.com -o get-docker.sh`
  - `sudo sh get-docker.sh`
- Install Minecraft Bedrock (https://hub.docker.com/r/itzg/minecraft-bedrock-server)
  - `docker volume create mc-volume`
  - `docker run -d -it --name mc-server -e EULA=TRUE -p 19132:19132/udp --restart unless-stopped -v mc-volume:/data itzg/minecraft-bedrock-server`
- Connect to Server-IP in Minecraft
- Done, and now:
  - Keep it running
  - Rescale (power off first)
  - Snapshot
  - Delete / Recreate from Snapshop => works immediatly, might have other IP
