# 아이템45 devDependencies에 typescript와 @types 추가하기

### Q1. 타입스크립트 프로젝트에서 typescript와 @types 패키지를 devDependencies에 추가해야하는 이유는 무엇인가요? 그리고 어떻게 추가할 수 있나요? (경민)
- 타입 관련 라이브러리들은 런타임에 실제 실행이 되지 않기 때문에 devDependencies에 있어야 한다.
- `npm install --save-dev`를 이용해서 설치하면 된다.
