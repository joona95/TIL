# AWS EC2 스왑 메모리 할당

## 문제 상황

- AWS EC2 프리티어 버전에서 Spring Boot 프로젝트 build 하면 메모리 문제로 76%쯤에서 서버가 멈추는 현상 발생

    - t2.micro의 RAM은 1GB 밖에 되지 않음

- 좀 속도가 느려지더라도 서버가 멈추지 않도록 스왑 메모리 할당을 해주기로 함

### 스왑 메모리란?

- 실제 메모리 RAM이 가득 찼지만 더 많은 메모리가 필요할 때 디스크 공간을 이용하여 부족한 메모리를 대체할 수 있는 공간을 의미함

- 실제 디스크 공간을 메모리처럼 사용하므로 가상 메모리라고 보면 됨

- 실제 메모리가 아닌 하드디스크를 이용하는 것이므로 메모리 속도면에서는 현저히 떨어짐

## 해결 방안

```
$ sudo dd if=/dev/zero of=/swapfile bs=64M count=16 //dd명령어를 사용한 리툭스 파일시스템에 스왑 파일 생성
$ sudo chmod 600 /swapfile //스왑 파일에 대한 읽고쓰기 권한 부여
$ sudo mkswap /swapfile //스왑 영역을 설정
$ sudo swapon /swapfile //스왑 영역을 추가해주기
$ sudo vi /etc/fstab //재부팅 시 스왑 설정 알려주기 위한 파일시스템 정보 변경. 진입 이후 최하단에 '/swapfile swap swap defaults 0 0' 추가
$ free -h //설정된 스왑 확인
```

- bs : 포맷의 단위

- count : 횟수 (블록수)

- mkswap 명령어 : swap 파일로 포맷

- swapon : swap 메모리 활성화

- swapoff : swap 메모리 비활성화