---
title: "[Github] github profile 꾸미기"
categories:
  - github
tag:
  - github
toc: true
toc_sticky: true
toc_label: "깃 허브 계정 꾸미기"
author_profile: true
sidebar:
  nav: "docs"
date:   2022-07-03 12:00:00
lastmod : 2022-07-03 12:00:00
sitemap :
  changefreq : daily
  priority : 1.0
---
개발자 혹은 개발자를 꿈꾸는 사람이면 git, github는 어디서 한번 쯤은 들어봤을 겁니다. <br>
그 중 github은 분산 버전 관리 툴인 git를 사용하는 프로젝트를 지원하는 웹 호스팅 서비스 <br>
**쉽게 말해 코드 저장소이라고 생각하시면 됩니다.**

따라서 다른 사람이 코드를 보기 위해 github에 들어 올 수 있는데 그 중 눈에 보이는 profile를 꾸미는 방법을 알아 보려고 합니다.
꾸미는 방법은 여러 가지 있겠지만 **'저의 github 프로필에 사용 하고 있는 것들만'** 소개 해드리려고 합니다.

![image](/assets/post/2022-07-03-git-profile-adornment-01/git_profile.png)
<p align="center" style="font-size: 12px">github 프로필</p>

## 1. 레퍼지토리 생성하기
### 본인 github 계정이름과 같은 이름으로 레퍼지토리를 만들기
![image](/assets/post/2022-07-03-git-profile-adornment-01/profile_repository.png)

`✔️ 중요: Add README.md를 체크 해주세요.`{: .notice--info}

## 2. README.md 수정
생성 되었으면 레퍼지토리에 README.md 파일에 자신에 입맛에 맛게 수정하면 됩니다.
<br>
기본 적으로 보통 **짧은소개, 스킬, sns주소 등**의 정보를 넣는게 많아 저도 한번 그렇게 해보겠습니다.

### markdown 작성
README는 일반적으로 마크다운 확장명을 사용하게 됩니다. 마크다운은 일반적으로 미리보기를 제공하지 않아 필자는 Webstorm을 사용하여 마크다운 편집을 사용하고 있습니다.<br>


`✔️ WebStorm은 30일 까지 무료이지만 다시 지우고 다운 받으시면 됩니다.`{: .notice--info}


찾아보니 [https://dillinger.io/](https://dillinger.io/) 웹 사이트에서도 가능하더라구요. 웹 사이트에서 하셔도 됩니다!

### Header 작성
README에 코드로 해더를 꾸밀 수 있지만 저는 마크다운 문법을 잘 알지 못하여 오픈 소스를 <br> 
이용하여 만들었습니다.  
>출처 : [https://github.com/kyechan99/capsule-render](https://github.com/kyechan99/capsule-render)

![header](https://capsule-render.vercel.app/api?type=cylinder&color=auto&height=300&section=header&text=HELLO&fontSize=90)

### 아이콘 선택
간단한 아이콘을 이용하여 깔끔하게 표시가 가능합니다.
> 출처: [https://shields.io/](https://shields.io/) , [https://simpleicons.org/](https://simpleicons.org/)

밑 문서대로 입력을 하시면 뱃지가 생성 되는 것을 확인 할 수 있습니다.
```html
<img src="https://img.shields.io/badge/Python-3766AB?style=flat-square&logo=Python&logoColor=white"/></a>&nbsp
```

## 3. 방문자 수 확인
방문자 수를 보여줄 수 있습니다.
> 출처 : [https://hits.seeyoufarm.com/](https://hits.seeyoufarm.com/)

![image](/assets/post/2022-07-03-git-profile-adornment-01/hit_ex.png)

[![Hits](https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fgithub.com%2FHyungMinKims&count_bg=%23C83D3D&title_bg=%23000000&icon=ko-fi.svg&icon_color=%23B00000&title=hits&edge_flat=true)](https://hits.seeyoufarm.com)

## 4. git stats 표시
Git Stats는 자신이 깃에서 어떤 활동을 하고 있는지 자세히 보여주는 지표입니다.
> 출처 : [https://pgmjun.tistory.com/21](https://pgmjun.tistory.com/21)

```markdown
![아이디's github stats](https://github-readme-stats.vercel.app/api?username=아이디&show_icons=true)
```
아래의 출처에서 가져와 사용할 수 있습니다. 흰색 말고 다른 스타일도 있으니 맘에 드는 것으로 사용해보세요.

> 출처 : [https://github.com/anuraghazra/github-readme-stats](https://github.com/anuraghazra/github-readme-stats)
 
![HyungMinkims's GitHub stats](https://github-readme-stats.vercel.app/api?username=HyungMinkims&show_icons=true&theme=dracula)

## 마무리
github profile를 간단하게 꾸미는 법을 알아봤습니다. 다른 좋은 방법이 있으면 같이 공유해줬으면 감사 하겠습니다.