# 아이템41 any의 진화를 이해하기

### Q1. 다음 두 예제에서 any가 어떻게 진화하는지 설명해주세요. (경민)

```ts
// 예제1
let value1;
value1 = { name: "경민" };
value2 = [41, 882, 3];
value = new Map();
value = () => "함수";

// 예제2
let value2: any;
value2 = 100;
value2 = "TypeScript";
value2 = [123, 234, 321];
value2 = { language: "typescript" };
```
