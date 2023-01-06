---
layout: post
title: GIT 블로그 만들기 3
subtitle: Jekyll 테마 적용하기
categories: study
tags: Git jekyll blog
---

GIT 블로그를 만들기 위해   
- GIT 저장소 및 페이지 생성
- 로걸과 GIT 저장소 연결
- 블로그 사이트를 만들 Jekyll 및 Ruby 설치    
  
단계까지 완료하였다. 이제부터는 내 취향에 맞게 블로그를 예쁘게 꾸미고, 포스팅을 하기 위한
Jekyll 테마를 다운로드하여 적용까지 해볼 예정이다. 

### Jekyll 테마 다운   
Jekyll 테마는 아래의 사이트들에서 다운로드 받을 수 있다.   
예쁜 무료 테마도 여러 개 있으니, 취향에 맞는 테마로 잘 찾아보자!  

[jekyll-themes.com/free](https://jekyll-themes.com/free/)

[themes.jekyllrc.org](http://themes.jekyllrc.org/)

[http://jekyllthemes.org/](http://jekyllthemes.org/)
  
나는 Yat Another Theme이라는 테마를 다운받았다.   
깔끔한 편이라 내 취향에 잘 맞을 것 같았다
![Yat Another Theme ](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/e5897a74-120e-45f2-b626-3d23e2a92440/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230105%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230105T051013Z&X-Amz-Expires=86400&X-Amz-Signature=e62d2235e50e4f4322ab9c9c634018d835f6ffd2c95e9fd7f56530f93d5a8835&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject "Yat Another Theme" )

### 테마 적용 방법

**1)  원하는 테마를 다운받고 압축을 푼다**

![빨간 줄에 있는 파일 다운로드! ](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/7b85147b-d865-42e5-97f4-ab49621f1ed1/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230105%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230105T051847Z&X-Amz-Expires=86400&X-Amz-Signature=1d64ee1ed3ae09379251793036fffe9223972547739c3cc40030d23875917509&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject)


빨간 줄에 있는 파일 다운로드! 

**2)  다운로드 파일 내의 모든 파일을 복사해서 미리 지정해둔 로컬 저장소 위치에 덮어씌운다.**


![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/f64f800e-24cb-48d0-9ed2-ad9b5669242f/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230105%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230105T051907Z&X-Amz-Expires=86400&X-Amz-Signature=472e83c295c851802d11d9dae485be9586d5b2a2e5bfc065f17e84a24d751d70&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject)
  
변경 내용을 GIT에 푸시하기 전에, 덮어 씌운 폴더가 잘 동작하는지 확인한다. Terminal에 아래 명령어를 입력한다.
```bash
bundle execjekyll serve
```  
해당 명령어는 추후에 블로그 내용을 변경하거나 POST를 작성할 때 내용을 미리 확인하는 용도로 자주 사용하게 된다!  
  
**3)  덮어 쓴 폴더 내용(변경사항) 을 git에 commit / push 한다.**

테마가 로컬에서 잘 적용된 것을 확인했다면 Terminal에 아래 명령어를 입력하여 Git 저장소에 변경사항을 푸시한다. 혹은 VSCode의 `Source Control` 기능을 이용하면 마우스 클릭만으로도 푸시가 가능하다.  
```bash
git add -A
git commit -m "new theme"
git push
```
  
### 테마 적용 결과

[https://hansjoo24.github.io/](https://hansjoo24.github.io/)

몇분 후 내 블로그 주소로 접속하면 테마가 적용된 것을 확인할 수 있다! 

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/0fe66031-bb40-49c8-9d7a-4abdc6a0105e/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230105%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230105T052842Z&X-Amz-Expires=86400&X-Amz-Signature=b2630b34b642deacc886f5d8e7d7154c20959494b9363e15b3a6756f79686543&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject)

* 하지만 아직 블로그 이름, 이미지 등의 구체적인 부분들은 적용이 되지 않은 상태이다.   
   
테마를 덮어씌운 로컬 저장소 폴더의 일부 파일을 찾으면 블로그 이름, 배너 이미지 파일 등을 바꿀 수 있다.  
내가 다운로드 받은 Yat Another Theme의 경우 디렉토리 내 `data/defaults.yml`, `_config.yml` 에서 수정이 가능했다. 테마 별로 폴더 내용은 조금씩 다르므로, 테마 설명을 참조하거나 직접 찾아보는 것이 필요하다.  
  
  아무튼 이것 저것 수정한 결과 만들어진 내 최종 블로그이다 

  ![result](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/0b090358-392e-468c-91b9-1b33a7b3c835/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230106%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230106T030056Z&X-Amz-Expires=86400&X-Amz-Signature=5105a27126ac26bd90be6328159406339567fc9bdf16e868bcbf0b5a1a01bc99&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject)

  아직은 게시글도 없어서 휑한 느낌이기는 한데, 앞으로 일상이나 공부 근황? 등 여러가지 내용을 추가해서 채워볼 계획이다! 