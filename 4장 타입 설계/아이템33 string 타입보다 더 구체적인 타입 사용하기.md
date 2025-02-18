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
