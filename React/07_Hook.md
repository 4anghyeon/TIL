# Hook

## useState 사용하기
- 컴포넌트에서 동적인 값을 상태(state)라고 부른다. useState라는 함수를 사용하여 컴포넌트에서 상태를 관리할 수 있다.
- e.g code
    ``` javascript
    function Counter() {
        const  [number, setNumber] = useState(0);

        const onIncrease = () => {
            setNumber(number+1);
        }

        const onDecrease = () => {
            setNumber(number-1);
        }


        return (
            <div>
                <h1>{number}</h1>
                <button onClick={onIncrease}>+1</button>
                <button onClick={onDecrease}>-1</button>
            </div>
        )
    }
    ```
- useState를 사용 할 때는 상태의 기본값을 파라미터로 넣어서 호출한다. 
- <b>여기서 첫번째 원소는 현재 상태, 두번째 원소는 Setter 함수이다.
> **_NOTE:_**  풀어쓰면 <br>
const numberState = useState(0); <br>
const number = numberState[0]; <br>
const setNumber = numberState[1]; <br>
이지만  배열 비구조화 할당을 통해 [number, setNumber] = useState(0)과 같이 가져올 수 있었다.

- number라는 값을 넣어주는 것이 아니라 이전 값을 가져오고 싶다면 다음과 같이도 가능하다.
``` javascript
  const onIncrease = () => {
    setNumber(prevNumber => prevNumber + 1);
  }

  const onDecrease = () => {
    setNumber(prevNumber => prevNumber - 1);
  }
```
>**_NOTE:_** 여기서 prevNumber => prevNumber + 1은 useState함수 안에서 정의 된 것으로 prevNumber에는 무조건 이전 값이 들어간다. (변수명이 preveNumber가 아니라 다른거여도 상관없다.)


---


## useRef로 특정 DOM 선택하기
- Javascript에서 특정 DOM을 선택 할 때 getElementById나 jquery에서 $()를 사용했다.
- 리액트에서도 특정 DOM을 선택해야 하는 상황이 있는데 그 때는 `ref` 를 사용한다.

``` javascript
import React, { useState, useRef } from 'react';

function nameInput() {
    const nameInput = useRef();

    const onReset = () => {
        setInputs({
        name: '',
        nickname: ''
        });
        nameInput.current.focus(); // ref = {nameInput} 으로 선언된 곳을 찾아서 focus해준다.
    };

    return (
    <div>
      <input
        name="name"
        placeholder="이름"
        onChange={onChange}
        value={name}
        ref={nameInput}
      />
      <button onClick={onReset}>초기화</button>
    </div>
  );
}
```

## useRef로 변수 선언하기
- `useRef`는 DOM을 선택하는 용도 외에도, 다른 용도가 하나 더 있다. 바로, 컴포넌트 안에서 조회 및 수정할 수 있는 변수를 관리하는 것이다.
- `useRef`로 관리하는 변수는 값이 바뀐다고해서 컴포넌트가 렌더링 되지 않는다. 
- `useRef`로 관리 할 수 있는 값...
  - setTimeout, setInterval을 통해 만들어진 `id`
  - 외부 라이브러리를 통해 생성된 인스턴스
  - scroll 위치