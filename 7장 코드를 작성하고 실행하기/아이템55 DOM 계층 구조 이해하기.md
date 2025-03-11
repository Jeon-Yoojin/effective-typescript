# 아이템55 DOM 계층 구조 이해하기

###Q1. 다음 함수의 오류부분과 오류를 수정해주세요(수영)
```
function handleDrag(eDown: Event) {
  const targetEl = eDown.currentTarget;
  targetEl.classList.add("dragging");
  const dragStart = [eDown.clientX, eDown.clientY];
  const handleUp = (eUp: Event) => {
    targetEl.classList.remove("dragging");
    targetEl.removeEventListener("mouseup", "handleUp");
    const dragEnd = [eUp.clientX, eUp.clinetY];
    console.log(
      `dx, dy`,
      [0, 1].map((i) => dragEnd[i] - dragStart[i])
    );
  };

  targetEl.addEventListener("mouseup", handleUp);
}
```
