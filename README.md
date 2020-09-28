# Vanilla Redux

## Redux 규칙

1. State를 직접 수정하지 않는다.

## 2020.09.28

`yarn add redux`

```javascript
// store란? => data를 모아두는 곳!
import { createStore } from "redux";

const add = document.getElementById("add");
const minus = document.getElementById("minus");
const number = document.querySelector("span");

// reducer는 데이터를 modify!
const countModifier = (count = 0, action) => {
  switch (action.type) {
    case "ADD":
      return count + 1;
    case "MINUS":
      return count - 1;
    default:
      return count;
  }
};

// Store를 생성
const countStore = createStore(countModifier);

const onChange = () => {
  number.innerText = countStore.getState();
};

//subscribe는 변화가 일어날 때 호출되는 메서드
countStore.subscribe(onChange);

const handleAdd = () => {
  // countModifier에 action으로 {type: "ADD"} 객체가 들어간다
  countStore.dispatch({ type: "ADD" });
};

const handleMinus = () => {
  countStore.dispatch({ type: "MINUS" });
};

add.addEventListener("click", handleAdd);
minus.addEventListener("click", handleMinus);
```
