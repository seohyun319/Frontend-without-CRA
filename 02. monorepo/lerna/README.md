# mono repo with lerna + yarn

- Babel 개발자에 의해 개발돼 CRA, Next.js, jest, storybook 등 많은 곳에 사용됨.
- 저수준의 Yarn, npm 위에 있는 고수준 레이어
  - Yarn으로 모노레포 구성 시 여러 workspace의 버전 관리, 테스트, 빌드, 배포, 게시 등의 작업은 일일이 구성해야 → Lerna는 이러한 작업을 최적화함

## Lerna 기반 프로젝트 생성

CLI를 쉽게 사용하기 위해 글로벌로 설치
`npm install --global lerna`
프로젝트를 Lerna로 초기화
`lerna init`
