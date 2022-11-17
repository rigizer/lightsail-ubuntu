# lightail-ubuntu 한줄 명령어
- 복사 후, SSH 클라이언트에 ```마우스를 이용해서 붙여넣기``` 하세요. ```Ctrl + V 사용불가```
- 설치가 끝난 경우, ```INSTALL COMPLETE```이 뜨면서, 설정이 완료됩니다.
```
cd && git clone https://github.com/rigizer/lightsail-ubuntu && chmod -R +x lightsail-ubuntu && ./lightsail-ubuntu/install.sh
```

<br/>

# lightsail-ubuntu 스크립트 세부설정
- 미러서버 변경 ```카카오 서버, https://mirror.kakao.com```
- apt 리스트 업데이트 ```sudo apt-get update```
- apt 리스트 업그레이드 ```sudo apt-get upgrade```

- tomcat9 설치, open-jdk11 설치
- tomcat9 포트변경 ```8080 -> 80```
- webapps 폴더 권한변경 ```777, rwxrwxrwx```

- MariaDB 설치
- MariaDB 외부접속 설정 ```127.0.0.1 -> 0.0.0.0```
- MariaDB root 계정 비밀번호 변경 ```ssafy0708```
- MariaDB root 계정 외부접속 설정
- MariaDB 서버시간을 ```UTC-0```에서 한국 표준시인 ```UTC-9```으로 변경

<br/>

# lightsail-ubuntu 사용방법

1. AWS에 접속하여 로그인 후 Lightail 페이지를 접속합니다.
  - https://lightsail.aws.amazon.com
<img src="https://user-images.githubusercontent.com/68414303/202434907-0fc78fa6-5567-40f3-bb1d-3874c0f9a405.png" width="500px"/>

<br/>

2. 인스턴스 위치: 서울, Linux 플랫폼, OS 전용을 누른 뒤, Ubuntu 20.04 LTS를 선택합니다.
<img src="https://user-images.githubusercontent.com/68414303/202435349-746852c1-fab5-4d97-94e3-9e7c24db73b1.png" width="500px"/>

<br/>

3. 원하는 인스턴스 플랜을 선택한 뒤, 인스턴스 이름을 지정합니다.
  - 여기서는 예시로, $3.5짜리 [512MB RAM/1 vCPU, 20GB SSD, 1TB Up/Down Traffic] 플랜을 선택했습니다.
<img src="https://user-images.githubusercontent.com/68414303/202436284-4be15a56-4810-477d-b5e9-6861978aab71.png" width="500px"/>

<br/>

4. 설정을 완료했다면, **인스턴스 생성** 버튼을 눌러 우분투 인스턴스를 생성합니다.
<img src="https://user-images.githubusercontent.com/68414303/202436747-b4fc4425-b160-4fb8-b01a-789c426cdd0c.png" width="500px"/>

<br/>

5. 우분투 인스턴스가 자동으로 생성됩니다. 생성이 완료되었다면 추가 설정을 하기 위해 인스턴스 설정 페이지로 접속해주세요.
<img src="https://user-images.githubusercontent.com/68414303/202438470-2d2cb5aa-44e9-46ff-9a6f-49e8ade7b632.png" width="500px"/>

<br/>

6. 네트워킹 메뉴로 접속합니다
<img src="https://user-images.githubusercontent.com/68414303/202438943-a4c52513-40d8-4eaa-a27c-22eb24bd9710.png" width="500px"/>

<br/>

7. MariaDB를 사용하기 위해, 3306 외부 포트번호에 대한 방화벽을 열어줍니다.
  - IPv4 방화벽 메뉴에서 규칙추가를 누른 뒤, [사용자 지정, TCP, 3306]을 입력하고 [생성]을 눌러줍니다.
  - 생성을 누른 뒤, 로딩이 끝나고 방화벽 규칙에 등록이 되었는지 확인합니다.
<img src="https://user-images.githubusercontent.com/68414303/202439390-532b1b9f-120c-42ff-a85d-67df13e75475.png" width="500px"/>

<br/>

8. SSH를 이용하여 우분투 인스턴스에 접속합니다.
    - 웹 SSH를 이용하려면 아래의 [SSH를 사용하여 연결] 버튼을 눌러줍니다
    - SSH 클라이언트를 이용한다면, **자체 SSH 클라이언트 사용**에서, [기본 키 다운로드] 버튼을 눌러 private key를 다운로드 받습니다
      + 해당 키는 절대 공유 및 분실하지 않도록 주의합니다
      + SSH 클라이언트 접속시 접속 명령어는 다음과 같습니다
        * (접속예시이며, 본인의 private key 파일경로와, 인스턴스 아이피를 입력하세요)
        ```
        ssh -i (private key 파일이름) -p 22 ubuntu@(인스턴스 아이피)
        ssh -i LightsailDefaultKey-ap-northeast-2.pem -p 22 ubuntu@192.168.0.1
        ```
<img src="https://user-images.githubusercontent.com/68414303/202440249-40fb05ec-048b-4a6b-a819-94bf6f6d041f.png" width="500px"/>
<img src="https://user-images.githubusercontent.com/68414303/202441666-98e182ba-c315-426c-a546-012a755cd570.png" width="500px"/>

<br/>

9. SSH 클라이언트에 접속했다면, 아래의 명령어를 붙여넣고, 엔터키를 눌러주세요
  - 명령어를 붙여넣을 때, ```Ctrl + V```를 이용하지 말고, ``마우스 오른쪽 버튼을 누른 뒤, 붙여넣기 버튼을 눌러``` 명령어를 입력합니다.
  ```
  cd && git clone https://github.com/rigizer/lightsail-ubuntu && chmod -R +x lightsail-ubuntu && ./lightsail-ubuntu/install.sh
  ```
<img src="https://user-images.githubusercontent.com/68414303/202444608-bd0c7b48-b8c6-49b5-9b85-fd4bb4cce08a.png" width="500px"/>

<br/>

10. 설치가 끝난 경우, ```INSTALL COMPLETE```이 뜨면서, 설정이 완료됩니다.
<img src="https://user-images.githubusercontent.com/68414303/202444980-469b9a81-69b3-49a4-92f8-07a3d2ca5b4c.png" width="500px"/>

