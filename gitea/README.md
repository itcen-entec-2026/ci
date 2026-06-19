# Gitea 구축

## 도커 엔진 설치

RHEL에 Docker Engine 설치하기

https://docs.docker.com/engine/install/rhel/

---

이전 버전을 제거하세요
```
sudo dnf remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine \
                  podman \
                  runc
```

---

rpm 저장소를 사용하여 설치하세요
```
sudo dnf -y install dnf-plugins-core
sudo dnf config-manager --add-repo https://download.docker.com/linux/rhel/docker-ce.repo
```

---

Docker Engine 설치

---

root 사용자로 로그인 전환
```
su - root
```

`1. Docker 패키지를 설치하세요.`

최신
```
sudo dnf install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

특정 버전

특정 버전을 설치하려면 먼저 저장소에서 사용 가능한 버전 목록을 확인하세요.
```
dnf list docker-ce --showduplicates | sort -r
```

패키지 이름(예: docker-ce)과 버전 문자열(두 번째 열)을 하이픈(-)으로 구분한 전체 패키지 이름을 사용하여 특정 버전을 설치하십시오. 예를 들어, docker-ce-3:29.6.0-1.el9입니다.

<VERSION_STRING> 부분을 원하는 버전으로 바꾸고 다음 명령어를 실행하여 설치하십시오.
```
sudo dnf install docker-ce-<VERSION_STRING> docker-ce-cli-<VERSION_STRING> containerd.io docker-buildx-plugin docker-compose-plugin
```

---

`2. Docker Engine을 시작합니다.`

```
sudo systemctl enable --now docker
```

---

`3. hello-world 이미지를 실행하여 설치가 성공적으로 완료되었는지 확인하십시오.`

```
sudo docker run hello-world
```

---

Docker Engine의 Linux 설치 후 단계

https://docs.docker.com/engine/install/linux-postinstall/

루트 사용자가 아닌 사용자로 Docker를 관리하세요

Docker 그룹을 생성하고 사용자를 추가하려면 다음 단계를 따르세요.

`1. docker 그룹을 생성합니다.`
```
sudo groupadd docker
```

`2. 사용자를 docker 그룹에 추가하세요.`
```
sudo usermod -aG docker god
```

`3. sudo 없이 Docker 명령어를 실행할 수 있는지 확인하십시오.`

god 사용자로 로그인 셸을 시작하며 전환
```
su - god
```

```
docker run hello-world
```

---

## 기테아 설치

https://docs.gitea.com/installation/install-with-docker

https://docs.gitea.com/installation/install-with-docker#basics

스타트업

Docker Compose 기반 설정을 시작하려면 `docker compose up -d` 명령을 실행하여 Gitea를 백그라운드에서 실행하세요. `docker compose ps` 명령을 사용하면 Gitea가 제대로 시작되었는지 확인할 수 있습니다. 로그는 `docker compose logs` 명령으로 볼 수 있습니다.

설정을 종료하려면 `docker compose down` 명령을 실행하세요. 그러면 컨테이너가 중지되고 종료됩니다. 볼륨은 그대로 유지됩니다.

SQLite

```
cd /home/god/gitea/gitea-1-Basics
docker compose up -d
```

http://localhost:3000/

```
cd /home/god/gitea/gitea-2-Ports
docker compose up -d
```

```
cd /home/god/gitea/gitea-3-MySQL_database
docker compose up -d
```

```
cd /home/god/gitea/gitea-4-PostgreSQL_database
docker compose up -d
```

```
cd /home/god/gitea/gitea-5-Named_volumes
docker compose up -d
```

---
