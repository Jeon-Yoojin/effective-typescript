# 아이템39 any를 구체적으로 변형해서 사용하기

### Q1. 객체를 표현하는 세 가지 타입 any와 object, {[key:string]: any}의 차이점이 무엇일까요? (유진)
- any: 모든 값을 허용. 
- object: 객체타입을 의미, 원시값(number, string)을 넣을수 없다. 
- {[key:string]: any}: 객체지만 Type을 구체적으로 정의 키의 타입이 string, 밸류가 any인 객체의 타입을 의미.
- object 와 {[key:string]: any} 차이점: object는 key를 열거는 가능하나 속성에 접근 불가, {[key:string]: any}는 속성에 접근 가능.
