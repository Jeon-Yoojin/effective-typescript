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

### Q2. 자바스크립트에서 this 바인딩을 하는 방법은 어떤 게 있나요? (유진)
