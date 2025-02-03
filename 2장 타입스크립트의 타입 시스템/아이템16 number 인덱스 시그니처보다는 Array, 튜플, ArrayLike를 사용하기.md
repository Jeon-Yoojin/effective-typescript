# 아이템16 number 인덱스 시그니처보다는 Array, 튜플, ArrayLike를 사용하기

### Q1. 다음 코드를 어떻게 개선하는 게 좋을까요? (경민)

```js
type ExampleArray = {
  [index: number]: string;
};

const arr: ExampleArray = { 0: "A", 1: "B", 2: "C" };
```
