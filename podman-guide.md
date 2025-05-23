## 📄 podman-guide

# Podman - Container Management in Linux

Podman is a container engine similar to Docker, but daemonless and rootless by design.

---

## 📦 1. Install Podman

### CentOS / RHEL:
```bash
sudo yum -y install podman

##🚀 2. Basic Podman Commands

Check version

podman --version

Search for images

podman search nginx

Pull an image

podman pull nginx

List images

podman images

Run a container

podman run -d -p 8080:80 nginx

List running containers

podman ps

Stop and remove a container

podman stop <container_id>
podman rm <container_id>

Remove an image

podman rmi nginx

## 🧱 3. Build Image from Containerfile

Create Containerfile:

FROM alpine
CMD ["echo", "Hello from Podman"]

Build the image:

podman build -t hello-podman .

## 🔒 4. Rootless Containers

Run container without root:

podman run -it --rm alpine sh

## 🧰 5. Podman vs Docker

| Feature             | Podman          | Docker  |
| ------------------- | --------------- | ------- |
| Daemon              | No (daemonless) | Yes     |
| Root required       | No (rootless)   | Yes     |
| CLI Compatible      | Yes             | Yes     |
| Systemd Integration | Yes             | Limited |

## ✅ Summary

| Command          | Description                    |
| ---------------- | ------------------------------ |
| `podman run`     | Run a container                |
| `podman ps`      | Show running containers        |
| `podman build`   | Build image from Containerfile |
| `podman images`  | Show local images              |
| `podman stop/rm` | Stop/remove container          |
| `podman rmi`     | Remove image                   |
