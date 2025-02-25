# 아이템42 모르는 타입의 값에는 any 대신 unknown을 사용하기

### Q1. any와 unknown의 차이에 대해 설명해주세요. (경민)

### Q2. 두 개의 단언문을 분리하는 상황에서 리팩토링을 해야 한다면 더 안전한 타입 단언 방법을 말해주세요. 그 이유는 무엇인가요? (유진)
```ts
declare const foo: Foo;
let barkAny = foo as any as Bar;
let barkUnk = foo as unknwon as Bar;
```
