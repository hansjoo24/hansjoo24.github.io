---
layout: post
title:  GIT 블로그 만들기 1
subtitle: GIT 저장소 생성과 로컬 저장소 연결
date:   2023-01-03 11:11:23 +0900
categories: study
tags: Git jekyll blog
---
이번에 처음으로 GIT 블로그를 만들어 보았다!   
처음이라 오류도 엄청 많이 걸리고 힘들었지만, 일단 다 만드니 뿌듯하다!   
그런 의미에서 내가 블로그를 만들었던 과정을 공유하고자 한다. (GIT / Jekyll 이용) 


GIT 블로그를 만들기 위해서는 

1. GIT의 저장소 / 호스팅할 페이지 생성
2. 해당 저장소를 로컬에서 변경(Add, commit, push) 하기 위한 리모트 연결 

이 필요하다. 

### VSCode 다운로드

이제부터 진행될 과정들에서,  VSCode를 이용하여 작업했다. VSCode는 아래 페이지에서 다운로드 받을 수 있다. 

[Download Visual Studio Code - Mac, Linux, Windows](https://code.visualstudio.com/download)

VSCode 다운로드 페이지

### GIT 저장소 생성하기

[GitHub: Let's build from here](https://github.com/)

GitHub 페이지

위의 GitHub Site에서 `Create a new repository` 를 눌러 저장소를 생성한다. (Public!) 

Repository 이름은 `(사용자id).github.io` 로 정했다. 대부분 다 이런 이름으로 정하는 것 같다. 

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/082b5360-1131-402f-9f3d-c4ec89c92c1e/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230103%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230103T041528Z&X-Amz-Expires=86400&X-Amz-Signature=d073ad0c91209f85679d3a46d3b6f33871abeb34d5a7cd44b62a82d02019c0d0&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject)

처음 실행한 경우 이러한 화면이 나올 텐데, `Quick setup`이나 `command line`을 통해 초기 설정을 한다. 아예 처음 만드는 경우 command line 부분을 다 복사해서 cmd/터미널(원하는 폴더 있는 곳) 에 붙여 넣으면 된다. 

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/398e3a00-9906-4281-8e5d-fd001934387b/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230103%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230103T042142Z&X-Amz-Expires=86400&X-Amz-Signature=b04f6f85089338133c6f5320e2fa2d4d192ec6e59a9cad51567a57643f4530a6&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject)

초기 설정을 완료하면 이렇게 된다. 우측 상단의 code 버튼을 누르면 로컬 저장소에 clone 할 수 있는 링크를 볼 수 있다. (HTTPS / SSH) 

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/80be130b-0940-46b0-bbba-16cd1e7defe1/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230103%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230103T042205Z&X-Amz-Expires=86400&X-Amz-Signature=0612a03bf4011672d023b2fa8a631457b2d4e8b4352790a5e35051a1843cde1f&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject)

나의 경우, HTTPS로 clone 했을 때, 변경사항을 push 한 경우 push 할 권한이 없다고 떠서, 이를 해결하기 위해 SSH로 clone을 진행했었다. SSH로 clone 하기 위해서는 사전에 SSH키를 생성하는 과정이 필요하다. 

### SSH키 생성 과정

(HTTPS 주소로 clone 할 경우 해당 과정은 건너 뛰어도 된다.) 

SSH를 이용하면 username/password를 이용하지 않아도 되기 때문에 민감한 비번을 노출하는 행위를 줄일 수 잇다! 그리고 미리 등록해두면 편리하게 GIT에 접근할 수 있어 한 번의 설정으로 쉽게 작업이 가능하다 !

우선, 터미널에서 SSH공개키와 개인키를 생성한다.

** SSH키를 만들기 전에 이미 키가 만들어져 있는지 확인해보는 작업이 필요하다고 한다. 키를 추가 발급했을 때 기존 키가 덮어씌워질 수 있기 때문!

SSH키는 일반적으로 `C:\Users\(사용자계정)\.ssh` 에 있고, id_rsa / is_rsa.pub 이런 파일이 있으면 이미 키가 있는 것이다! 

만약 키가 없다면, ssh-keygen 명령어를 이용해 생성할 수 있다. 

```bash
ssh-keygen 
Enter file in which to save the key (/c/Users/(사용자계정)/.ssh/id_rsa)
// SSH키 위치 입력 
```

다음에는 SSH 키에 대한 비밀번호를 추가로 지정할 지 물어보는데, 비밀번호를 저장할 필요가 없다면 그냥 엔터 2번 누르면 된다. 

나의 경우 처음에 폴더가 없었어서 no repository 떴다가 같은 명령어를 다시 입력했더니 생성되었다.

키가 잘 생성되었다면, `C:\Users\(사용자계정)\.ssh` 여기에서 확인 가능하다. 
생성된 파일 중 is_rsa.pub 파일을 메모장으로 열고, 안의 내용을 복사한다. 

[https://github.com/settings/keys](https://github.com/settings/keys)

Github의 Setting-SSH key 항목으로 들어가 .New SSH key를 누른 다음, Key 내용에 방금 복사했던 내용을 붙여넣는다. 

마지막으로, 로컬에서 GIT 저장소를 clone할 때 SSH 링크로 연결하면 된다 ! 

### 로컬 - GIT 저장소 연결하기 (Clone)

VSCode상단 File - Open Folder을 눌러, 내가 페이지를 수정, 커밋할 로컬 저장소의 위치를 지정해서 열어준다. 나는 `C:\Users\(사용자)\blog` 의 위치로 설정했는데, 잘한건지는 나도 모르겠따 

상단의 Terminal - New Terminal 을 눌러 터미널을 연다. 여기서 GIT 명령어를 이용하여 맨 처음에 만든 Git 저장소를 Clone 해오면 된다. 

clone은 HTTPS 프로토콜 / SSH 프로토콜 2가지로 할 수 있으며, 나는 SSH로 진행했다. 

```bash
git clone git@github.com:hansjoo24/hansjoo24.github.io.git
```

clone 이 성공적으로 진행되었다면, 기존 디렉토리에 [hansjoo24.github.io](http://hansjoo24.github.io) (본인 저장소 이름) 폴더가 추가된 것을 볼 수 있다. 

또한, 초반에 저장소를 생성할 때 READ ME 파일을 생성해 두었다면 READ ME 파일도 나타날 것이다. 이제 이 폴더에 원하는 내용을 넣고 터미널에서 commit / push 를 하면 그 내용이 GIT 저장소와 페이지에 반영될 것이다   

다음 포스팅 GIT 블로그 만들기 2편에서는 본격적으로 블로그를 만들기 위한 Ruby, Jekyll 설치 및 적용 방법에 대해 포스팅할 예정이다! 