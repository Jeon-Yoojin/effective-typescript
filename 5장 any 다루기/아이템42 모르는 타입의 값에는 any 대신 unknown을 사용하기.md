# 아이템42 모르는 타입의 값에는 any 대신 unknown을 사용하기

### Q1. any와 unknown의 차이에 대해 설명해주세요. (경민)
- any 타입은 다른 타입으로도 할당이 가능하지만, unknown은 다른 타입으로 할당이 불가능.
- any 타입 변수에 다른 타입을 주면 method가 사용 가능하지만 unknown은 사용 불가능.
- unKnown은 타입검증이 필요한 타입, any는 타입 검증을 하지 않음.

### Q2. 두 개의 단언문을 분리하는 상황에서 리팩토링을 해야 한다면 더 안전한 타입 단언 방법을 말해주세요. 그 이유는 무엇인가요? (유진)
```ts
declare const foo: Foo;
let barkAny = foo as any as Bar;
let barkUnk = foo as unknown as Bar;
```
let barkUnk = foo as unknwon as Bar가 더 안전 이유는 unknown의 경우는 분리되는 즉시 오류를 발생하게 되므로 더 안전합니다.
any는 타입체크의 기능이 사라진다. unKnown은 타입검사를 통해 다른 타입시 error 발생

```
let foo: number = 42;

// 1. unknown로 변환
let temp: unknown = foo;

// 2. unknown를 원하는 타입으로 변환
let bar: string = temp; //즉시 에러 (any의 경우는 가능)
```
