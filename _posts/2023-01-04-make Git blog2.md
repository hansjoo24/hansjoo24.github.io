---
layout: post
title: GIT 블로그 만들기 2
subtitle: Ruby / Jekyll 설치
categories: study
tags: Git jekyll blog
---

### Ruby / Jekyll 설치   

이전에는 GIT 저장소 및 페이지를 생성하고, 로컬과 GIT 저장소를 연결하여 작업할 수 있는 환경을 만들었다면, 이번에는 본격적으로 블로그를 만들기 위해 Ruby , Jekyll를 설치해보고자 한다! 

### Jekyll

Jekyll은 Ruby 언어를 기반으로 만들어진 설치형 블로그로, 마크다운 언어를 사용해서 포스트를 작성하면 HTML로 변환하여 정적 사이트를 만들어준다. Github를 통한 무료 호스팅이 가능하며, **다양한 테마를 쉽게 적용할 수 있기 때문에!** 첫 블로그를 Jekyll로 만들기로 결정했다 ㅎㅎ

### Ruby 설치

Jekyll를 이용하기 위해서는 Ruby를 먼저 설치하는 것이 필요하다. 

루비 공식 홈페이지에 최신 버전을 다운받는다. 

[Downloads](https://rubyinstaller.org/downloads/)

Ruby+Devkit 3.1.3-1(x64) 로 다운

- 나는 3.2.0-1로 처음에 다운받았었는데 왜인지 모르게 계속 오류가 떠서 루비쪽에서도 가장 추천하는 3.1.3 버전으로 다운받았다.

![요론 화면이 뜨면 그냥 엔터 누르면 된다(1~3까지모두설치) ](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/94839834-af57-4118-93dc-b2db5340f7a4/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230104%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230104T004617Z&X-Amz-Expires=86400&X-Amz-Signature=40588c4c7dcd10ebc8801ececaed72d1ef918581089325470631e21b9e4b90ba&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject)

요론 화면이 뜨면 그냥 엔터 누르면 된다(1~3까지모두설치) 

++ Ruby를 삭제하고 재설치할 때 계속 오류가 뜰 때가 있는데 (ㅠㅠ) 제어판에서 프로그램 제거를 하고, 로컬디스크C에서 Ruby 폴더를 삭제한 다음, 재부팅을 하고 cmd 및 vscode 터미널에서 `ruby -v` 를 입력하여 루비가 삭제되었는지 제대로 확인한 다음 나머지를 설치해야 문제없이 돌아간다 ! 

### Jekyll 설치과정

(모두 클론한 폴더 내 터미널에서 진행 / vscode)

```plain
ruby -v 
gem install jekyll
gem install jekyll bundler
gem install github-pages
```

`jekyll -v` 로 설치가 잘 되었는지 확인 후 아래 단계를 진행한다.

```plain
jekyll new./ 
```

```plain
bundle install
```

```plain
bundle exec jekyll serve
```

해당 명령어를 통해 서버를 띄우는데 성공하면 서버 주소를 보여준다.

→ 서버 주소 브라우저에 입력 시 Jekyll 블로그를 확인할 수 있다! 

### 변경 내용 Git에 Push

로컬에 jekyll 을 설치하여 블로그를 만드는 데까지 성공했으면, 
이 내용을 Git에도 업로드하여야 한다 ! 

로컬(VScode 터미널)에서 아래 명령어를 입력한다. 

```plain
git add -A 
git commit -m "New Blog"
```

`git status` 로 파일 add가 잘 되었는지
`git log`를 통해 커밋이 잘 되었는지 확인 가능하다. 

커밋이 잘 되었다면 Git 저장소에 해당 커밋을 Push 한다.

Git 저장소와 로컬 저장소는 원격으로 연결되어 있으므로, `git push`를 날려줘야 로컬 저장소에서 남겨 놓은 변경 이력들이 원격 저장소로 전송된다.  

```plain
git push -u origin main 
git push
```

- `-u` 옵션은 인자 생략을 하기 위한 것으로, 한번 -u옵션을 써서 push를 했다면, 다음부터는 `git push` 만 입력해도 이전과 똑같은 방식으로 push 하는 것이 가능하다!

git push가 성공적으로 완료되었다면

내 git 저장소 및 블로그 페이지를 방문해 내용이 변경되었는지 
확인하면 된다