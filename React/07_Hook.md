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