# 아이템53 타입스크립트 기능보다는 ECMAScript 기능을 사용하기

### Q1. 다음 열거형을 타입스크립트의 역활을 명확하게 하려면 어떻게 변경하는게 좋을까요?(수영)
```
enum Flavor {
    VANILLA = 'vanilla',
    CHOCOLATE = 'chocolate',
    STRAWBERY = 'strawberry'
}
```

### Q2. 문자열 열거형 타입(enum)을 사용한 다음 코드가 타입 오류가 나는 이유는 무엇인가요? (유진)
```ts
/* enum Flavor - Q1을 참고 */
let flavor = Flavor.CHOCOLATE;

flabor = 'strawberry';
          ~~~~~~~~~~~
```
