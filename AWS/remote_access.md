# AWS EC2 원격 접속 및 파일 업로드 (Mac OS)

## AWS EC2 인스턴스 원격 접속

```
ssh -i <키페어 경로> ec2-user@<퍼블릭 DNS주소>
```
```
ssh -i key.pem ec2-user@ec2-15-165-165-250.ap-northeast-2.compute.amazonaws.com 
```

## AWS EC2에 로컬 컴퓨터 파일 업로드

```
scp -i <키페어 경로> <전송할 파일 경로> ec2-user@<퍼블릭 DNS주소>:<전송할 EC2 경로>
```

