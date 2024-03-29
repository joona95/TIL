# AWS 서버 연결 도메인 port 숨기기 (포트 포워딩)

## 문제

- IP와 도메인 연결 후 'https://도메인:포트번호'로 특정 포트를 기입해야 했는데 포트 번호 없이 접속하고 싶었음

# 포트 포워딩

- 포트 포워딩이란 외부에서 접속한 IP주소와 포트 번호를 내부 호스트에 다시 매핑하는 것

## 해결방안

1. EC2 쉘 접속

2. 포트포워딩 정보 입력

```
sudo iptables -A PREROUTING -t nat -i eth0 -p tcp --dport <들어오는포트번호> -j REDIRECT --to-port <내보내는포트번호>
```

- <들어오는포트번호>로 들어오는 요청은 <내보내는포트번호>로 들어온 요청으로 변환

- 포트포워딩: 전달받은 패킷에 IP:Port 정보를 포트 포워딩 설정 정보 참고하여 특정 IP:Port로 변환시켜주는 기능. 주로 공유기에서 외부 IP로 들어온 Port에 따라 어떤 기기(내부IP)에 연결시켜줄지 결정할 때 필요함.

- 들어오는 포트: http는 80, https는 443

```
sudo iptables -t nat -L --line-numbers
```

- 포트포워딩 확인

- 포트포워딩은 우선순위가 있어 dport가 똑같은게 있다면 상위포트가 우선순위로 적용됨.

```
sudo iptables -t nat -D PREROUTING <삭제할번호>
```
- 포트포워딩 삭제

- 포트포워딩 확인 시 번호(num) 입력

```
sudo iptables -F -t nat
```

- 포트포워딩 초기화