# 아이템16 number 인덱스 시그니처보다는 Array, 튜플, ArrayLike를 사용하기

### Q1. 다음 코드를 어떻게 개선하는 게 좋을까요? (경민)

```ts
type ExampleArray = {
  [index: number]: string;
};

const arr: ExampleArray = { 0: "A", 1: "B", 2: "C" };
```

- number 인덱스 시그니처를 사용하고 있다.

```ts
const arr: string[] = ["A", "B", "C"];

const arr: Array<string> = ["A", "B", "C"];
```

- 이런 식으로 정의하는 것이 더 좋은 것 같다. (인덱스 숫자에 특별한 의미가 있는 것이 아니기 때문)
