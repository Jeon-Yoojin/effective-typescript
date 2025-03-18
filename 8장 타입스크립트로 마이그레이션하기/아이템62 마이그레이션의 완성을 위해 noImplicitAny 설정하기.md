# 아이템62 마이그레이션의 완성을 위해 noImplicitAny 설정하기

### Q1. 다음 코드에서 noImplicitAny 설정 유무에 따른 차이를 설명해 주세요.(수영)

```ts
class Chart {
  indices: number[];

  getRanges() {
    for (const r of this.indices) {
      const low = r[0];
      const high = r[1];
    }
  }
}
```

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
