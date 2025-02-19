# 아이템33 string 타입보다 더 구체적인 타입 사용하기

### Q1. 객체의 속성 값을 가져오는 함수가 있습니다. 이 함수의 문제점은 무엇인가요? (경민)

```ts
const user = {
  id: 1,
  name: "Alice",
  age: 25,
};

function getProperty(obj: object, key: string) {
  return obj[key];
}

const name = getProperty(user, "name");
const email = getProperty(user, "email");
```
### Q2. Album의 recodingType이 'studio', 'live' 두 가지일 경우 다음 interface의 문제점과 개선방안을 말해주세요 (수영)
```ts
interface Album {
    artist : string;
    title: string;
    releaseDate: string;
    recordingType: string;
}
```
