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

- Readonly는 얕게 동작함.
- room 안의 카운트 필드를 직접 수정하는 건 되는데, room 객체 자체를 바꾸면 오류남.
- 1번은 안되고 2번은 된다. 얕게 동작하기 때문에.
