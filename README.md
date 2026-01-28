# Container Infra Auto Deployment with ![Ubuntu](https://img.shields.io/badge/Ubuntu-24.04-orange?logo=ubuntu&logoColor=white) ![Ansible](https://img.shields.io/badge/Ansible-2.16-blue?logo=ansible&logoColor=white)

**Ansible + Docker로 컨테이너 인프라 자동 배포**
- Nginx 웹서버 (2 Replicas) → 8080, 8081
- MariaDB 데이터베이스 → 3306
- API 서버 (Nginx) → 8000
- Docker Network (infra-net) → 컨테이너 간 연결

**Ubuntu**

↓ Docker 설치

↓ Ansible (infra.yml)

↓ GitHub Actions (.github/workflows/deploy.yml)

├─ web-0 (Nginx 웹)

├─ web-1 (Nginx 웹)

├─ database (MariaDB)

└─ api (Nginx API)

## Docker 설치
```bash
sudo apt remove --purge containerd containerd.io docker.io -y
sudo apt autoremove -y
sudo apt update
sudo apt install -y docker.io
```

## Docker 설정
```bash
sudo systemctl start docker
sudo systemctl enable docker
sudo usermod -aG docker $USER && newgrp docker
```

## Ansible 설치
```bash
sudo apt install -y ansible-core
ansible-galaxy collection install community.docker
```

## 배포
### 자동
- deploy.yml 수정 → Commit changes

<img alt="image" src="https://github.com/user-attachments/assets/56cff9d7-656d-4d0d-9a0d-52a9b719abf2" width="1000"/>

### 수동
- Actions → Run workflow

<img alt="image" src="https://github.com/user-attachments/assets/5e065bdf-0763-45d1-9d57-52605b707163" width="1000"/>
