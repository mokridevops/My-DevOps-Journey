
# Kubernetes:
<img width="652" height="329" alt="image" src="https://github.com/user-attachments/assets/05cad8cd-4f92-48e5-910b-f10be8fe6ef5" /> <br>


<img width="247" height="179" alt="image" src="https://github.com/user-attachments/assets/9f6c2a3d-6217-49f7-a733-2d43ed321d54" />


### Docker installation instructions:

sudo dnf -y install dnf-plugins-core
sudo dnf config-manager --add-repo https://download.docker.com/linux/rhel/docker-ce.repo -y
sudo dnf install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
sudo systemctl enable --now docker
sudo usermod -aG docker ec2-user

<img width="943" height="524" alt="image" src="https://github.com/user-attachments/assets/5468ea65-1b92-4baf-9068-ac16efcdbf4e" />

### eksctl installation instructions:
# for ARM systems, set ARCH to: `arm64`, `armv6` or `armv7`
ARCH=$(uname -m | sed 's/x86_64/amd64/' | sed 's/aarch64/arm64/')
PLATFORM=$(uname -s)_$ARCH
curl -sLO "https://github.com/eksctl-io/eksctl/releases/latest/download/eksctl_$PLATFORM.tar.gz"
tar -xzf eksctl_$PLATFORM.tar.gz -C /tmp && rm eksctl_$PLATFORM.tar.gz
sudo install -m 0755 /tmp/eksctl /usr/local/bin && rm /tmp/eksctl

Note: we are adding eksctl to /usr/local/bin -> that means it will be globally accessible.



