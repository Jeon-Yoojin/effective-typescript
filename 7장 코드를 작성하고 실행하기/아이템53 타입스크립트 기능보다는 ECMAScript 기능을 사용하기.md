# 아이템53 타입스크립트 기능보다는 ECMAScript 기능을 사용하기

### Q1. 다음 열거형을 타입스크립트의 역활을 명확하게 하려면 어떻게 변경하는게 좋을까요?(수영)
```ts
enum Flavor {
    VANILLA = 'vanilla',
    CHOCOLATE = 'chocolate',
    STRAWBERY = 'strawberry'
}
```

```ts
type Flavor = 'vanilla' | 'chocolate' | 'strawberry';

위처럼 리터럴 타입 유니온 타입으로 정의하면 됩니다.
```

### Q2. 문자열 열거형 타입(enum)을 사용한 다음 코드가 타입 오류가 나는 이유는 무엇인가요? (유진)
```ts
/* enum Flavor - Q1을 참고 */
let flavor = Flavor.CHOCOLATE;

flavor = 'strawberry';
          ~~~~~~~~~~~
```

타입스크립트에서 문자열 열거형 타입(enum)을 사용하면, 구조적 타이핑이 아닌 명목적 타이핑을 하기 때문에, 이름이 같지 않아서 에러가 나는 것 같습니다.
enum 타입은 해당 enum의 멤버 값만 허용하며, 같은 값이라도 직접 문자열을 할당할 수는 없다.


- 에러가 안 나게 하려면? 

1.

```ts
flavor = Flavor.STRAWBERY;
```

이런 식으로 enum에 .으로 접근해서 할당

2. 유니온 타입으로 정의하기.