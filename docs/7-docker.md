# 7. Installing Docker
If you want, you can check docker documentation for ubuntu: : [https://docs.docker.com/engine/install/ubuntu/](https://docs.docker.com/engine/install/ubuntu/)

## 7.1 Add Docker repositories
Copy bash scripts below and paste them to SSH terminal. Note you might need to paste text using 
SHIFT + INSERT. Press ENTER after scripts are pasted to terminal. Monitor terminal output. If prompted yes or no, write yes or y and press ENTER


Run the following:

    # Add Docker's official GPG key:
    sudo apt update
    sudo apt install ca-certificates curl
    sudo install -m 0755 -d /etc/apt/keyrings
    sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
    sudo chmod a+r /etc/apt/keyrings/docker.asc

    # Add the repository to Apt sources:
    sudo tee /etc/apt/sources.list.d/docker.sources <<EOF
    Types: deb
    URIs: https://download.docker.com/linux/ubuntu
    Suites: $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}")
    Components: stable
    Signed-By: /etc/apt/keyrings/docker.asc
    EOF

    sudo apt update

---

## 7.2 Install Docker
Copy bash scripts below and paste it to SSH terminal. Note you might need to paste text using 
SHIFT + INSERT. Press ENTER after scripts are pasted to terminal. Monitor terminal output. If prompted yes or no, write yes or y and press ENTER.

    sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
