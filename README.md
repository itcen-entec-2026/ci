# ci
CI/CD 구축

## GitLab 설치

### GitLab 설치 요구 사항

VirtualBox 버전 7.2.0 r170228 (Qt6.8.0 on windows)
- Storage: 100 GB
- CPU: 2 vCPU
- Memory: 8 GB

VirtualBox 설정
- 포트 포워딩: 80
- Windows Hosts 파일 위치
```
C:\Windows\System32\drivers\etc
```
- Windows Hosts 파일 수정 (GitLab 도메인 매핑)
```
127.0.0.1 gitlab.example.com
```

### AlmaLinux 및 RHEL 호환 배포판에 Linux 패키지를 설치하세요.

필수 조건
- Red Hat Enterprise Linux 9, Rocky-9.7-x86_64-minimal.iso

Firewalld(방화벽 서비스) 서비스 상태 확인
```bash
systemctl status firewalld
```

Firewalld(방화벽 서비스) 서비스 중지
```bash
systemctl stop firewalld
```

Firewalld 서비스 자동 시작 비활성화
```bash
systemctl disable firewalld
```

GitLab 패키지 저장소를 추가합니다.
- Enterprise Edition
```bash
curl --location "https://packages.gitlab.com/install/repositories/gitlab/gitlab-ee/script.rpm.sh" | sudo bash
```

패키지를 설치하세요
```bash
GITLAB_ROOT_EMAIL="admin@example.com" GITLAB_ROOT_PASSWORD="strongpassword" EXTERNAL_URL="https://gitlab.example.com" dnf install gitlab-ee
```

gitlab-ee 19.0.2-ee.0.el9
- gitlab-ee-19.0.2-ee.0.el9.x86_64
```bash
===============================================================================================================================================================================================
 꾸러미                                                  구조                              버전                                              저장소                                       크기
===============================================================================================================================================================================================
설치 중:
 gitlab-ee                                               x86_64                            19.0.2-ee.0.el9                                   gitlab_gitlab-ee                            1.0 G
```

서비스 상태 확인:
```bash
gitlab-ctl status
```

---

GitLab 설치 요구 사항
- https://docs.gitlab.com/install/requirements/
- GitLab installation requirements

경우에 따라 GitLab은 최소 8GB의 메모리로 실행될 수 있습니다.
- https://docs.gitlab.com/install/requirements/#memory
- In some cases, GitLab can run with at least 8 GB of memory.

AlmaLinux 및 RHEL 호환 배포판에 Linux 패키지를 설치하세요.
- https://docs.gitlab.com/install/package/almalinux/
- Install the Linux package on AlmaLinux and RHEL-compatible distributions

필수 조건
- https://docs.gitlab.com/install/package/almalinux/#prerequisites
- Prerequisites

GitLab 패키지 저장소를 추가합니다.
- https://docs.gitlab.com/install/package/almalinux/#add-the-gitlab-package-repository
- Add the GitLab package repository

패키지를 설치하세요
- https://docs.gitlab.com/install/package/almalinux/#install-the-package
- Install the package

## GitLab 설정
