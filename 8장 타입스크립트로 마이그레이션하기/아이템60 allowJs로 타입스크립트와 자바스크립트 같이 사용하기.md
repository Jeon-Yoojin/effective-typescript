# 아이템60 allowJs로 타입스크립트와 자바스크립트 같이 사용하기

### Q1. 다음은 유닛 테스트 도구 중 하나인 jest의 jest.config.js 설정 일부입니다. 정규식이 의미하는 것이 무엇인지 설명해주세요. (경민)

```js
module.exports = {
  transform: {
    "^.+\\.tsx?$": "ts-jest",
  },
};
```
