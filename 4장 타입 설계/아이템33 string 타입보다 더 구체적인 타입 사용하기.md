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
- 동작하지 않는다 (name은 잘 동작하지만, email은 오류가 난다)
- key로 받을 수 있는 타입이 너무 넓기 때문 (string)
- object 타입 대신 이렇게
```ts
function getProperty<T, K extends keyof T>(obj: T, key: K): T[K] {
  return obj[key];
}
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
- recordingType의 타입을 'studio' | 'live'로 지정한다.
- 또는 RecordingType을 만들어서 'studio' | 'live'를 새로운 타입으로 만들어서 사용
- releaseDate의 타입도 string보다는 Date를 사용하도록 변경
