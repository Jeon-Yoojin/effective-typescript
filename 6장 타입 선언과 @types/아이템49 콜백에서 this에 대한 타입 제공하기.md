# 아이템49 콜백에서 this에 대한 타입 제공하기

### Q1. 다음 Class 의 this 바인딩 문제를 해결하는 방법 두가지를 제시해 주세요 (수영)
```
class ResetButton {
  render() {
    return makeButton({ text: "Reset", onClick: this.onClick });
  }
  onClick() {
    alert(`Reset${this}`);
  }
}
```
- 생성자 constructor(){} 를 이용해서 바인딩을 해준다.
- `call`메소드를 이용해서 바인딩을 해준다.
- () => {} 를 이용해서 바인딩을 해준다.


** class 형태로 api 타입을 정의하는 방법이 있다

### Q2. 자바스크립트에서 this 바인딩을 하는 방법은 어떤 게 있나요? (유진)
- call이나 apply, bind 메소드를 사용해서 특정 개체를 this로 지정 `함수.call(객체)` (명시적 바인딩)
- 화살표 함수를 사용한다. 화살표 함수의 정적 스코프에서 this를 바인딩한다. (렉시컬 바인딩)
- 객체 내에 있는 메소드를 호출할 때 메소드를 호출한 객체가 this가 된다. (묵시적 바인딩)
- 클래스에서 this 바인딩 (bind, 화살표 함수)
