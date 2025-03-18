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
