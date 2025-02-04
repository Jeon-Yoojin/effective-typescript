# 아이템17 변경 관련된 오류 방지를 위해 readonly 사용하기

### Q1. 다음 코드에서 알 수 있는 사실은 무엇인가요? (경민)

```js
interface Home {
  room: {
    count: number,
  };
}

const myHome: Readonly<Home> = { room: { count: 3 } };
myHome.room = { count: 4 };
myHome.room.count = 4;
```
