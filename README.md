# 모두의 만든 이 웹사이트

판교고등학교 창체동아리 ‘모두의 만든 이’를 소개하는 Jekyll 정적 웹사이트입니다. 기존 테마에 동아리 소개 콘텐츠와 한국어 설정을 적용한 과거 작업입니다.

## 목적과 구현 범위

동아리의 문제의식과 모집 안내를 웹으로 전달하기 위한 사이트입니다. [소개 글](_posts/2021-03-15-모두의-만든-이-소개.md)을 중심으로 홈·아카이브·태그 화면을 구성합니다. 소개 글에 적힌 향후 프로젝트나 하드웨어 구상이 이 저장소에 구현되어 있다는 뜻은 아닙니다.

- Markdown 소개 글과 이미지·영상 삽입
- Jekyll 레이아웃을 이용한 글 목록·상세·아카이브·태그 화면
- 한국어 메뉴와 사이트 설정
- `tetris/`에 포함된 별도 원작 게임 코드

## 실제 화면과 데모

[동아리 사이트](https://modoomaker.github.io/)에서 소개 글을 열 수 있습니다. 2026-11-13 Chrome에서 홈과 글 목록 렌더링을 확인했습니다. 화면의 동아리 안내는 2021년 자료이며 현재 모집이나 활동 상태를 나타내지 않습니다.

## 기술 스택과 구조

| 영역 | 구성 |
|---|---|
| 정적 사이트 | Jekyll, Liquid, Markdown, HTML, Sass/CSS, JavaScript |
| 테마 | 현재 파일은 NexT 구성, Muse scheme |
| 의존성 | Ruby/Bundler, Gemfile의 github-pages |
| 배포 | GitHub Pages |
| 별도 게임 | JavaScript, Gulp, Web Audio, Service Worker |

[_config.yml](_config.yml)이 제목·언어·메뉴·테마 설정을 관리하고, [_layouts/](_layouts/)가 페이지 틀, [_posts/](_posts/)가 콘텐츠를 담당합니다. 정적 생성으로 콘텐츠와 화면 틀을 나누며 별도 백엔드·DB는 없습니다.

## 원작과 작업 범위

GitHub 메타데이터상 이 저장소의 Fork parent는 [Hydejack](https://github.com/hydecorp/hydejack)입니다. 다만 현재 설정·레이아웃과 [기존 영문 문서](README.en.md)는 NexT Jekyll 테마를 가리킵니다. 현재 소스의 테마와 Fork 계보를 구분해야 합니다.

동아리 소개 콘텐츠·설정 작업과 테마·게임의 원작 구현을 구분합니다. 이 저장소를 테마 엔진이나 Tetris 자체를 새로 개발한 프로젝트로 소개하지 않습니다.

## 설치와 실행

Ruby와 Bundler가 필요합니다. 오래된 [Gemfile.lock](Gemfile.lock)을 사용하므로 현재 Ruby 환경에서 의존성 설치가 되는지는 별도 확인이 필요합니다.

```bash
git clone https://github.com/ModooMaker/ModooMaker.github.io.git
cd ModooMaker.github.io
bundle install
bundle exec jekyll serve
```

기본 주소는 `http://localhost:4000/`입니다. `tetris/`는 Jekyll과 별도 구성입니다. 게임 소스를 확인하려면 [게임 README](tetris/README.md)와 [package.json](tetris/package.json)을 참고하세요. 게임의 `npm test`는 실제 테스트가 아닌 기본 실패 스크립트입니다.

## 검증과 현재 한계

- 2026-11-13 공개 홈의 HTTP 응답과 Chrome 렌더링을 확인했습니다. Ruby 의존성 설치·Jekyll 빌드·게임 전체 동작은 다시 검증하지 않았습니다.
- 별도 자동 회귀 테스트나 저장소 내 Actions workflow는 없습니다.
- 자료와 의존성이 오래되어 외부 영상·CDN·링크·브라우저 호환성은 재확인이 필요합니다.
- 루트에 통합 LICENSE 파일은 없습니다. 하위 라이브러리·게임의 라이선스를 저장소 전체에 자동 적용하지 않습니다.

## 출처와 관련 링크

- [NexT Jekyll 원작](https://github.com/Simpleyyt/jekyll-theme-next), [Hexo NexT](https://github.com/iissnan/hexo-theme-next)
- [기존 영문 테마 안내](README.en.md)
- [Tetris 원작 — Eugene Tiurin](https://github.com/ytiurin/tetris), [게임 라이선스](tetris/LICENSE)

화면의 Jekyll·NexT 출처와 소스·이미지·하위 라이브러리의 기존 저작권 표기를 유지해야 합니다.
