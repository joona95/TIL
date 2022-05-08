# 포트 번호 없이 요청 처리받기

## 문제상황

- url 뒤에 포트 번호 따로 적지 않고 요청을 리다이렉트 시켜주고 싶었음


## 해결방안

- 현재 적용 상태 확인

```
sudo iptables -t nat -L
```


- 리다이렉트

```
sudo iptables -t nat -A PREROUTING -p tcp --dport <들어오는 port> -j REDIRECT --to-ports <리다이렉트할 port>
```

들어오는 포트: http는 80, https는 443


- 초기화

```
sudo iptables -F -t nat
```