# 아이템41 any의 진화를 이해하기

### Q1. 다음 두 예제에서 any가 어떻게 진화하는지 설명해주세요. (경민)

```ts
// 예제1
let value1;
value1 = { name: "경민" }; //object 
value1 = [41, 882, 3]; //object 
value1 = new Map(); //object
value1 = () => "함수"; // function
 
// 예제2
let value2: any;
value2 = 100; // any
value2 = "TypeScript"; //any
value2 = [123, 234, 321]; // any
value2 = { language: "typescript" }; //any
```

