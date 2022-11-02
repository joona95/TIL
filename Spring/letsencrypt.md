# LetsEncrypt 활용하여 Spring Boot에 무료 SSL 추가/갱신

## 1. Certbot 설치

```
sudo yum install certbot
```

## 2. Certbot 활용하여 도메인에 SSL 적용

```
sudo certbot certonly --standalone
```

- 이메일 입력 후 동의 절차 완료

- 마지막으로 SSL인증서 발급받고자 하는 도메인 입력

## 3. SSL인증서 발급 성공한 경우 Spring Boot에 적용

### 3-1. pem을 PKCS12 형식으로 변경

```
$ sudo su 
$ cd /etc/letsencrypt/live/도메인  #인증서발급위치로 이동
$ openssl pkcs12 -export -in fullchain.pem -inkey privkey.pem -out keystore.p12 -name 이름 -CAfile chain.pem -caname root #pem을 pkcs12형식으로 변경
$ mv keystore.p12 /home/ec2-user #생성한 key 파일을 홈디렉토리로 이동
$ chmod 777 keystore.p12 #스프링부트에서 읽을 수 있도록 권한 변경
```

- 해당 keystore.p12는 java 실행파일(jar) 위치로 이동 후 java 실행

### 3-2. 스프링 부트 설정에 인증서 적용

```
server:
    port: 9090
    ssl:
        enabled: true
        key-store: keystore.p12
        key-store-password: 비밀번호
        key-store-type: PKCS12
```

- application.yml에 인증서 적용 설정

## 4. Certbot 으로 SSL 인증서 갱신

```
$ sudo certbot certificates  #인증서 만료일 확인
$ sudo certbot renew --dry-run  #인증서 모의 갱신
$ sudo certbot renew  #인증서 실제 갱신
```

- 인증서 갱신을 위해 80, 443 포트 서비스 임시 중지

- 인증서 갱신 후 pem 인증서를 PKCS12 형식으로 변경

- 해당 keystore.p12는 java 실행파일(jar) 위치로 이동 후 java 실행

