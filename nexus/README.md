# Nexus Repository OSS 3.76.1 Docker Compose 구성

사용량 제한에 따른 강제 차단을 피하는 것이 목적이라면 Nexus Repository OSS 3.76.1이 사실상 마지막 선택지

## 실행

```
docker compose up -d
```

## 상태와 로그 확인

```
docker compose ps
```

```
docker compose logs -f nexus
```

## Nexus 초기 접속 및 Admin 비밀번호 확인

접속은 http://localhost:8081이며, 최초 admin 비밀번호는 다음으로 확인합니다.

```
docker exec nexus cat /nexus-data/admin.password
```
