# mono repo with yarn

## yarn 기반 프로젝트 생성

프로젝트를 yarn으로 초기화 → package.json 생성
`yarn init`

## workspace 추가

```json
{
  "name": "yarn",
  "version": "1.0.0",
  "main": "index.js",
  "license": "MIT",
  "workspaces": ["packages/*"]
}
```
