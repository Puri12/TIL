# Linux Mint 21 Docker Install

### 1. Update
```shell
sudo apt update
```
### 2. 도커 의존성 패키지 설치, 도커 오피셜 키 추가

```shell
sudo apt install apt-transport-https ca-certificates curl gnupg-agent software-properties-common

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

### 3. 도커 레파지토리 추가
```shell
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(. /etc/os-release; echo "$UBUNTU_CODENAME") stable"
```

### 4. 도커 설치
```shell
sudo apt update
sudo apt -y install docker-ce
```

### 5. 도커 버전확인
```shell
docker --version
```
