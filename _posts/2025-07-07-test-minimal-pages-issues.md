---
layout: single
title: test-minimal pages issues
date: 2025-07-07 19:57
category: 
author: Perplexity
tags: []
summary: 
---

```markdown
# 테스트-미니멀 GitHub Pages 설정 및 문제 해결 기록

## 1. 저장소 및 기본 구조

- 저장소 이름: `test-minimal` (Project Pages)
- 주요 폴더/파일 구조:
  - 루트: `index.md`
  - `_pages/`: `about.md`, `posts.md`
  - `_data/`: `navigation.yml`
  - `_posts/`: 블로그 글
  - `_config.yml`: 사이트 설정

---

## 2. 주요 설정 및 이슈 해결 과정

### 2.1. GitHub Pages 기본 경로 및 baseurl

- Project Pages는 반드시 `_config.yml`에 다음과 같이 설정:
  ```
  url: "https://shiene1010.github.io"
  baseurl: "/test-minimal"
  ```
- 메뉴, permalink, 실제 접속 경로 모두 baseurl(`/test-minimal`)을 포함해야 404 오류 방지

---

### 2.2. Minimal Mistakes 테마 적용

- `_config.yml`에서 `remote_theme`만 사용:
  ```
  remote_theme: "mmistakes/minimal-mistakes"
  ```
- `theme:` 줄은 반드시 삭제 또는 주석 처리

---

### 2.3. index.md(홈) 파일 관리

- 루트에 반드시 소문자 `index.md` 파일 존재
- 프론트매터 예시:
  ```
  ---
  layout: home
  title: "홈"
  ---
  ```
- 별도의 `permalink` 필요 없음

---

### 2.4. _pages 폴더와 개별 페이지

- `_pages/about.md`, `_pages/posts.md` 등은 반드시 루트의 `_pages/` 폴더에 위치
- `_config.yml`에 다음 설정 추가:
  ```
  include:
    - _pages
  ```
- 각 파일의 프론트매터 예시:
  - About:
    ```
    ---
    layout: single
    title: "About"
    permalink: /test-minimal/about/
    ---
    ```
  - Posts:
    ```
    ---
    layout: posts
    title: "Posts"
    permalink: /test-minimal/posts/
    ---
    ```

---

### 2.5. _data/navigation.yml 메뉴 구성

- 모든 메뉴 url은 baseurl을 포함한 절대경로로 작성:
  ```
  main:
    - title: "About"
      url: /test-minimal/about/
    - title: "Posts"
      url: /test-minimal/posts/
  ```

---

### 2.6. 404 에러 및 경로 문제

- 메뉴 url, permalink, baseurl이 하나라도 불일치하면 404 발생
- 루트에 index.md가 없거나, `_pages` 폴더 위치가 잘못되면 홈/페이지 404
- `_posts` 폴더의 포스트 파일은 반드시 `layout: single` 프론트매터 필요

---

### 2.7. YAML 문법 오류 및 빌드 실패

- `_config.yml`에서 콜론(:), 따옴표, 들여쓰기, 주석 위치 등 YAML 문법 엄수
- 댓글 등 필요 없는 옵션은 과감히 삭제
- 빌드 실패 시, GitHub Actions/Pages 로그의 마지막 에러 메시지 확인

---

### 2.8. 로컬 개발 환경과 remote_theme

- remote_theme 방식은 로컬에서 바로 적용되지 않음
- 로컬에서 테마 적용하려면:
  1. Gemfile에 `gem "jekyll-remote-theme"` 추가
  2. `_config.yml`에 `plugins: - jekyll-remote-theme` 추가
  3. `bundle install` 후 `bundle exec jekyll serve`로 실행
  4. 접속 경로는 `http://localhost:4000/test-minimal/`

---

### 2.9. 기타 실전 팁

- 메뉴에서 Home을 빼고 싶으면 navigation.yml에서 해당 항목만 삭제
- 마스트헤드 타이틀은 `_config.yml`의 `title:`로 변경
- 포스트가 흰 바탕에 텍스트만 나오면, `_posts/`의 모든 글에 `layout: single` 추가

---

## 3. 최종 구조 예시

```
<프로젝트 루트>/
  index.md
  _pages/
    about.md
    posts.md
  _data/
    navigation.yml
  _posts/
    2024-07-07-my-first-post.md
  _config.yml
  Gemfile
```

---

## 4. 자주 겪는 문제 & 해결법 요약

| 문제/현상                 | 원인 및 해결법 요약                                                  |
|--------------------------|---------------------------------------------------------------------|
| 404 에러                 | baseurl, permalink, 메뉴 url 불일치, index.md 위치 오류               |
| 메뉴/상단바 미출력        | navigation.yml 구조 오류, layout 미지정, 테마 설정 오류               |
| 빌드 실패(빨간 X)         | YAML 문법 오류, theme/remote_theme 중복, 파일명/경로 오류             |
| 포스트만 흰 바탕          | 프론트매터에 layout: single 누락                                    |
| 로컬에서 테마 미적용      | Gemfile, plugins 설정 누락, remote_theme 미설정                      |
| 메뉴 클릭 시 404          | 메뉴 url과 페이지 permalink 불일치                                   |

---

## 5. 참고

- Minimal Mistakes 공식 문서: https://mmistakes.github.io/minimal-mistakes/docs/
- Jekyll 공식 구조 안내: https://jekyllrb.com/docs/structure/
- YAML 문법 체크: https://www.yamllint.com/

---

**이 문서는 테스트-미니멀 GitHub Pages 구축 및 문제 해결 과정을 한눈에 볼 수 있도록 정리한 기록입니다.**
```

Sources
