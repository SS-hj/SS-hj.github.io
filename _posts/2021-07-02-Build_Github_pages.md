---
title: "Github pages 만들기 (Minimal Mistakes with utterances)"

category: Github

tag: 
 - Github pages
 - utterances
 - Minimal Mistakes

toc_label: "목차"

toc: true

header:
 teaser: /assets/images/image-20210620204209474.png


---



  <br/>

저는 많은 시행착오 끝에 Github pages를 성공적으로 구축하였지만, 이 포스팅을 보고 있는 여러분들은 제가 정리한 Step들만 따라가면서 하면 누구나 쉽게 깃블로그를 구축할 수 있도록 정리하였습니다! 

참고로 제가 선택한 테마는 Minimal Mistakes이며, utterances 기반의 댓글 위젯을 사용하였습니다.

  <br/>

  <br/>

## Step 1. 테마 선택 / 적용

  <br/>

(1) [http://jekyllthemes.org/](http://jekyllthemes.org/)에서 마음에 드는 테마를 선택합니다.  

테마를 선택해서 Demo로 샘플 형태를 확인해 볼 수 있습니다.

(2) 적용하고자 하는 테마가 정해졌으면, Homepage 버튼을 누릅니다.

![image-20210620204209474](/assets/images/image-20210620204209474.png)

(3) 그러면 해당 테마의 github repository가 뜨는데, 이때 아래 이미지와 같이 Code에서 Clone 부분의 HTTPS URL을 복사합니다.

![image-20210702001340348](/assets/images/image-20210702001340348.png)

(4) 로컬 컴퓨터의 최상위 폴더로 이동한 후, 위에서 복사한 URL을 git clone 뒤에 붙여넣어 선택한 테마를 복제뜹니다.

(참고로 저는 이 과정들을 Git bash에서 진행해주었습니다.)

```bash
$ cd ../../.. #최상위 폴더로 이동
$ git clone https://github.com/mmistakes/minimal-mistakes.git
$ cd minimal-mistakes
$ bundle
```

(5) Gemfile 파일에 내용 추가

```bash
# Windows does not include zoneinfo files, so bundle the tzinfo-data gem
gem 'tzinfo'
gem 'tzinfo-data', platforms: [:mingw, :mswin, :x64_mingw]
```

(6) bundle exec jekyll serve 입력 후, 127.0.0.1:4000에 들어가서 정상적으로 기본 블로그가 뜨면 완료

![image-20210701231600188](/assets/images/image-20210701231600188.png)

(위 bash창에 Ctrl+C를 누르면 로컬 블로그가 작동되고 있는 상태에서 나올 수 있습니다.)

(7) 그 후, 아래 이미지와 같이 Repository name이 "자신의 깃허브 ID.github.io"로 된 repository를 생성합니다.

![image-20210701230504139](/assets/images/image-20210701230504139.png)

(8) 이 minimal-mistakes 소스를 나의 레포지토리로 옮깁니다.

```bash
$ cd ..
$ mv minimal-mistakes/ [본인의 Github ID].github.io
$ cd [본인의 Github ID].github.io
$ git remote remove origin
$ git remote add origin [위에서 생성한 본인의 Github pages 레포지토리 HTTPS URL을 복붙] #본인의 Github pages 레포지토리를 가져와 현재 파일들을 옮김
$ git push -u origin master
```

![image-20210701233256739](/assets/images/image-20210701233256739.png)

<br/>



## Step 2. 파일들 수정하기

  <br/>

이 부분부터는 로컬에서 하셔도 되고, 온라인 상에서 하셔도 됩니다. 본인의 편의에 따라 진행해 주시면 됩니다.

참고로 로컬에서 업로드 할 때 Git 코드는 다음과 같습니다.

```bash
$ git pull   #온라인 서버에서 업로드 된 파일들을 로컬로 업데이트
$ git add .  #수정사항이 있는 파일들 전부 추가해서 묶음
$ git status #현재 git 상태 확인
$ git commit -m "주석"   #add로 묶었던 파일들에 이름을 붙여줌
$ git push -u origin master  #로컬 서버에서 온라인 서버로 데이터를 업로드
```

<br/>

* _config.yml 수정

  이 파일은 Jekyll 사이트 설정 옵션을 정의하는 파일입니다. 이 파일이 GIthub Pages 구축의 큰 틀을 담당한다고 할 수 있습니다.

  저는 아래 링크와 같이 코드를 수정해 주었습니다. (이때 저는 comments 부분을 한번에 커밋해주었습니다. 이 부분은 스킵하시고 아래  Step 3에서 따로 수정해주시면 됩니다. 아니면 저와 같은 댓글위젯과 테마를 사용하시려면 그대로 수정해주시면 됩니다!)

  [_config.yml 수정 코드](https://github.com/SS-hj/SS-hj.github.io/commit/6880093c3c43d8feeacc54a7db93d735a457a230#diff-ecec67b0e1d7e17a83587c6d27b6baaaa133f42482b07bd3685c77f34b62d883)

* _data/navigation.yml 수정

  ```ruby
  # main links
  main:
    - title: "About"
      url: /about/
    - title: "Categories"
      url: /categories/
    - title: "연도별 포스트"
      url: /year-archive/
    - title: "Tags"
      url: /tags/
    # - title: "About"
    #   url: https://mmistakes.github.io/minimal-mistakes/about/
    # - title: "Sample Posts"
    #   url: /year-archive/
    # - title: "Sample Collections"
    #   url: /collection-archive/
    # - title: "Sitemap"
    #   url: /sitemap/
  ```

* _pages/ 폴더 안에 navigation에서 생성한 블로그 상단 메뉴들을 설정하는 파일들 생성

  about.md

  ```ruby
  ---
  title: "About"
  layout: single
  permalink: /about/
  author_profile: true
  ---
  ```

  category-archive.md

  ```ruby
  ---
  title: "Posts by Category"
  layout: categories
  permalink: /categories/
  author_profile: true
  ---
  ```

  tag-archive.md

  ```ruby
  ---
  title: "Posts by Tag"
  permalink: /tags/
  layout: tags
  author_profile: true
  ---
  ```

  year-archive.md

  ```ruby
  ---
  title: "Posts by Year"
  permalink: /year-archive/
  layout: posts
  author_profile: true
  ---
  ```

  

  <br/>

## Step 3. 댓글 기능 추가 (utterances)

  <br/>

일반적으로는 Disqus를 기반으로 댓글기능을 추가하시는데, 이렇게 하면 해당 사이트에서 댓글을 확인해야하는 번거로움이 있습니다. 따라서, 저는 GitHub issue를 기반으로 한 댓글 위젯인 utterances를 이용하였습니다.

(1) https://github.com/apps/utterances 에서 utterance를 install 합니다.

이때 Only select repositories로 Github Pages의 댓글들을 알림받을 public 레포지토리를 따로 생성하여 지정해줍니다.

(2) 본인의 취향에 맞게 configuration를 작성합니다.

※ 이때 repo에는 위에서 지정한 public 레포지토리 주소를 적어야 합니다.

![image-20210626213248769](/assets/images/image-20210626213248769.png)

(3) configuration 작성 후, 자동으로 생성된 script문을 확인합니다.

![image-20210626213332128](/assets/images/image-20210626213332128.png)

(4) 3번의 script문을 바탕으로 _includes/comments-providers/utterances.html 파일을 수정합니다.

![image-20210628150244782](/assets/images/image-20210628150244782.png)

(5) _config.yml 파일에서 comments 부분을 수정합니다.

provider에 어느 댓글 위젯을 선택했는지 쓰고, 또 필요한 부분들을(theme과 issue_term) 추가로 수정해 줍니다.

(6) _posts/ 폴더 안에 테스트용 포스트 파일 생성하여 포스팅 한 후, 댓글을 테스트해봅니다.

(참고로, 파일이름은 "연도-월-일자-제목.md"으로 설정하여야 하며, 이때 제목 부분은 오류를 대비하여 가능한 영어로 짓는 것을 추천합니다. 파일 내용은 마크다운 문법을 따라 작성해야 합니다.)

![image-20210626213332128](/assets/images/image-20210627224540489.png)

댓글 기능이 잘 지원되고 있음을 확인할 수 있습니다.

  <br/>

  

## Step 4. 구글과 네이버에서 검색이 가능하게 설정

  <br/>

(1) sitemap 활성화

sitemap은 해당 블로그에 어떤 글들이 있는지 알려주는 역할을 합니다. 

_config.yml 파일에 아래 내용이 있는지 확인하시고, 없으시면 해당 코드를 추가해줍니다.

```ruby
plugins: ['jekyll-paginate', 'jekyll-sitemap', 'jekyll-include-cache', 'jekyll-gist']  #jekyll-sitemap이 추가되어 있어야 구글검색이 가능함
```

[sitemap.xml](https://github.com/SS-hj/SS-hj.github.io/blob/master/sitemap.xml) 파일을 자신의 github.io repository의 root에 생성합니다.

(3) robots.txt 생성

자신의 github.io repository의 root에 robots.txt를 추가하고 아래 내용을 수정하여 입력합니다.

```
User-agent: *
Allow: /
Sitemap: https://본인의 GitHub ID.github.io/sitemap.xml
```

(4) Google Search Console 에 sitemap 제출

- [https://search.google.com/search-console/welcome](https://search.google.com/search-console/welcome) 에서 URL 접두어 부분에 Github pages URL을 입력합니다.
- 계속 버튼을 누르면 뜨는 HTML 파일을 다운로드한 후, 자신의 github.io repository의 root에 업로드합니다.
- Google Search Console에서 본인의 github.io 속성을 선택한 후, 왼쪽 메뉴에 색인 Sitemaps에 들어갑니다.
- 새 사이트맵 추가에 뒷부분에 sitemap.xml을 입력한 후, 제출합니다.

(5) 네이버 Search Advisor에 sitemap 제출

- [https://searchadvisor.naver.com/](https://searchadvisor.naver.com/) 에서 웹마스터 도구 사용하기 클릭합니다.

- 본인의 Github Pages의 url을 입력 후, 제출합니다.

- 1번 부분의 초록색 글씨로 뜨는 "HTML 확인 파일"을 클릭하여 다운로드합니다.

  <img src = "/assets/images/image-20210628165538861.png" width="800px">

- 다운로드한 파일을 자신의 github.io repository의 root에 업로드합니다.

- 요청 > 사이트맵 제출 로 들어갑니다.

  <img src = "/assets/images/image-20210628165909762.png" width="800px">

- google과 마찬가지로 새로운 URL부분에 sitemap.xml을 입력한 후, 제출합니다.

  <img src = "/assets/images/image-20210628170225201.png" width="800px">

  

  <br/>

## Step 5. 추가적인 설정들

  <br/>

(1) 본문 글씨 크기 조정: _sass/minimal-mistakes/&#95;reset.scss 파일 수정

[글씨 크기 조정을 위한 파일 수정](https://github.com/SS-hj/SS-hj.github.io/commit/fbc4f37d550602f2aed6137aac70e34e65dede57#diff-95568912732a62bcb95b3d4fad8a1398ece6936b6b6beba61b339993f54efdd0)

(2) 프로필 이미지 업로드

- local에서 위에서 생성했던 본인의 Github pages 폴더 내의 assets 폴더에 images폴더를 만든 후, 프로필로 원하는 이미지를 올립니다.

- _config.yml 파일을 수정합니다.

  [프로필 변경을 위한 파일 수정](https://github.com/SS-hj/SS-hj.github.io/commit/a5c39a148930889402ead45fca02ebbafb60e8fd)

  


<br/>

<br/>

## 출처

[https://eeesnghyun.github.io/%EA%B0%9C%EB%B0%9C%EA%B3%BC%EC%A0%95/2020/01/04/post1.html](https://eeesnghyun.github.io/%EA%B0%9C%EB%B0%9C%EA%B3%BC%EC%A0%95/2020/01/04/post1.html)

[https://honbabzone.com/jekyll/start-gitHubBlog/](https://honbabzone.com/jekyll/start-gitHubBlog/)

[https://devinlife.com/howto/](https://devinlife.com/howto/)

[https://baek.dev/post/4/](https://baek.dev/post/4/)

[http://jinyongjeong.github.io/2017/01/13/blog_make_searched/](http://jinyongjeong.github.io/2017/01/13/blog_make_searched/)

[https://jennysgap.tistory.com/entry/Github-Pages-04-%ED%83%80%EC%9E%84%EC%A1%B4-%EA%B4%80%EB%A6%AC](https://jennysgap.tistory.com/entry/Github-Pages-04-%ED%83%80%EC%9E%84%EC%A1%B4-%EA%B4%80%EB%A6%AC)
