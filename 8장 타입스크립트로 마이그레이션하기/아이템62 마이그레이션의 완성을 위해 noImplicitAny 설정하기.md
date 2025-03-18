# 아이템62 마이그레이션의 완성을 위해 noImplicitAny 설정하기

### Q1. 다음 코드에서 noImplicitAny 설정 유무에 따른 차이를 설명해 주세요.(수영)

```ts
class Chart {
  indices: number[]; -> number[][] || [number, number][]

  getRanges() {
    for (const r of this.indices) {
      const low = r[0];
      const high = r[1];
    }
  }
}
```
- noImplicitAny 설정 X : 아무 문제없이 작동
- noImplicitAny 설정 O :const low = r[0] // 암시적 any : indices의 타입이 number[] 여서 r은 Number 타입이라 인덱스 시그니처 X
                        const high = r[1] // 암시적 any : 암시적 any : indices의 타입이 number[] 여서 r은 Number 타입이라 인덱스 시그니처 X
                     
### Q2. noImplicitAny를 활성화하면 다음 코드에서 어떤 오류가 발생할까요? 어떻게 수정하면 좋을까요? (경민)

```ts
function calculateTotal(items) {
  let total = 0;
  for (const item of items) {
    total += item.price * item.quantity;
  }
  return total;
}
```
item.price * item.quantity  암시적 any 에러 
function calculateTotal(items 암시적 any) 에러
const item of items 암시적 any 에러

해결
```ts
type Item = {
  price:number;
  quantity:number;
}

function calculateTotal(items: Item[]) {
  let total = 0;
  for (const item of items) {
    total += item.price * item.quantity;
  }
  return total;
}
```


