# Container Infra Auto Deployment with 

**Ansible + Docker로 컨테이너 인프라 자동 배포**
- Nginx 웹서버 (2 Replicas) → 8080, 8081
- MariaDB 데이터베이스 → 3306
- API 서버 (Nginx) → 8000
- Docker Network (infra-net) → 컨테이너 간 연결

**Ubuntu**

↓ Docker 엔진 설치

↓ 컨테이너 서버 생성 (Ansible)

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

## 배포 실행
```bash
ansible-playbook infra.yml
```
<img alt="image" src="https://github.com/user-attachments/assets/6a8278e4-02e7-440b-a1de-7b443a5c695b" width="800" />

## 검증
```bash
docker ps
```
<img alt="image" src="https://github.com/user-attachments/assets/3b0810ca-910c-4a23-82cb-651ca7b11df5" width="800"/>

```bash
curl localhost:8080
```
<img alt="image" src="https://github.com/user-attachments/assets/4e6bb267-fef9-4961-b072-9b4be1d452c7" width="800"/>
