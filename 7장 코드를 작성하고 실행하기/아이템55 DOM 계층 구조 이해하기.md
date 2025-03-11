# 아이템55 DOM 계층 구조 이해하기

### Q1. 다음 함수의 오류부분과 오류를 수정해주세요(수영)
```ts
function handleDrag(eDown: Event) {
  const targetEl = eDown.currentTarget;
  targetEl.classList.add("dragging");
  const dragStart = [eDown.clientX, eDown.clientY];
  const handleUp = (eUp: Event) => {
    targetEl.classList.remove("dragging");
    targetEl.removeEventListener("mouseup", handleUp);
    const dragEnd = [eUp.clientX, eUp.clientY];
    console.log(
      `dx, dy`,
      [0, 1].map((i) => dragEnd[i] - dragStart[i])
    );
  };

  targetEl.addEventListener("mouseup", handleUp);
}
```

오류:
```ts 
function handleDrag(eDown: Event) {
  const targetEl = eDown.currentTarget;
  targetEl.classList.add("dragging");
  // ~~~~~ targetEl 개체가 'null'인 것 같습니다.
  //       ~~~~~~~~~ 'EventTarget' 형식에 'classList' 속성이 없습니다.   
  const dragStart = [eDown.clientX, eDown.clientY];
                        // ~~~~~~ 'Event' 형식에 'clientX' 속성이 없습니다.
                        //                ~~~~~~ 'Event' 형식에 'clientY' 속성이 없습니다.
  const handleUp = (eUp: Event) => {
    targetEl.classList.remove("dragging");
  // ~~~~~ targetEl 개체가 'null'인 것 같습니다.
  //       ~~~~~~~~~ 'EventTarget' 형식에 'classList' 속성이 없습니다.   
    targetEl.removeEventListener("mouseup", handleUp);
    const dragEnd = [eUp.clientX, eUp.clientY];
                      // ~~~~~~ 'Event' 형식에 'clientX' 속성이 없습니다.
                            //        ~~~~~~ 'Event' 형식에 'clientY' 속성이 없습니다.
    console.log(
      `dx, dy`,
      [0, 1].map((i) => dragEnd[i] - dragStart[i])
    );
  };

  targetEl.addEventListener("mouseup", handleUp);
  // ~~~~~ 개체가 'null'인 것 같습니다.
}
```

답:
```ts
function handleDrag(eDown: MouseEvent) {
  if (!eDown.currentTarget) return;
  const targetEl = eDown.currentTarget as HTMLElement;
  targetEl.classList.add("dragging");
  
  const dragStart = [eDown.clientX, eDown.clientY];

  const handleUp = (eUp: MouseEvent) => {
    targetEl.classList.remove("dragging");
    targetEl.removeEventListener("mouseup", handleUp);
    const dragEnd = [eUp.clientX, eUp.clientY];

    console.log(
      `dx, dy`,
      [0, 1].map((i) => dragEnd[i] - dragStart[i])
    );
  };

  targetEl.addEventListener("mouseup", handleUp);
}
```